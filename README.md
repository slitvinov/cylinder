<h2>Karman Vortex Street</h2>

This repository uses
[Basilisk](http://basilisk.fr/src/INSTALL)
for simulating Karman vortex street phenomena. Follow these steps to install basilisk
<pre>
$ wget http://basilisk.fr/basilisk/basilisk.tar.gz
$ tar zxf basilisk.tar.gz
$ cd basilisk/src
$ cp config.gcc config
$ make ast && make qcc
$ cp qcc "$HOME/.local/bin/"
</pre>

Compile
<pre>
$ make
CC99=mpicc qcc -disable-dimensions -source  -D_MPI=1 cylinder.c
mpicc -o cylinder -O2 -g  _cylinder.c -lm
</pre>

Compile without basilisk:
<pre>
$ mpicc -O2 deploy/cylinder.c  -lm
$ mpiexec ./a.out -v -i -r 2000 -l 7 -m 10 -p 100 -e 10
</pre>

<pre>
$ ./cylinder -h
Usage: cylinder [-h] [-i] [-v] -r <Reynolds number> -l <resolution level> -p <dump period> -e <end time>
Options:
  -h     Display this help message
  -v     Verbose
  -i     Enable PPM image dumping
  -r <Reynolds number>     the Reynolds number (a decimal number)
  -l <num>    Minimum resolution level (positive integer)
  -m <num>    Maximum resolution level (positive integer)
  -p <dump period>         the dump period (positive integer)
  -e <end time>            end time of the simulation (decimal number)

Example usage:
  ./cylinder -v -i -r 100 -l 7 -m 10 -p 100 -e 2
</pre>
