---
title: "error on installing rmpi"
date: 2008-06-07
forum: Education &amp; Science
---

### Post by GreenLinux@R on 2008-06-07
Hello Ubuntu_R uers,

I am trying hard to get rmpi installed. I get the the package tarball ( rmpi_0.5-5.orig.tar.gz) from [http://packages.ubuntu.com/hardy/math/r-cran-rmpi](http://packages.ubuntu.com/hardy/math/r-cran-rmpi) and save into ~/R/i486-pc-linux-gnu-library/2.7, then use R CMD INSTALL rmpi_0.5-5.orig.tar.gz

BUT I got no luck

greenlinux4r@greenlinux4r-desktop:~/R/i486-pc-linux-gnu-library/2.7$ R CMD INSTALL rmpi_0.5-5.orig.tar.gzERROR: cannot extract package from 'rmpi_0.5-5.orig.tar.gz'

Does you know how to solve this problem? thx.

---

### Post by GreenLinux@R on 2008-06-07
libmpi is not found when I use a old version of the package 

greenlinux4r@greenlinux4r-desktop:~/R/i486-pc-linux-gnu-library/2.7$ R CMD INSTALL --clean Rmpi_0.5-4.tar.gz
* Installing to library '/home/greenlinux4r/R/i486-pc-linux-gnu-library/2.7'
* Installing *source* package 'Rmpi' ...
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
[COLOR="DarkRed"][B]checking mpi.h usability... no
checking mpi.h presence... no
checking for mpi.h... no
Try to find libmpi or libmpich ...
checking for main in -lmpi... no
libmpi not found. exiting...[/B][/COLOR]
ERROR: configuration failed for package 'Rmpi'
** Removing '/home/greenlinux4r/R/i486-pc-linux-gnu-library/2.7/Rmpi'
** Restoring previous '/home/greenlinux4r/R/i486-pc-linux-gnu-library/2.7/Rmpi'
greenlinux4r@greenlinux4r-desktop:~/R/i486-pc-linux-gnu-library/2.7$

---

### Post by GreenLinux@R on 2008-06-07
I flowed the solution  and used [COLOR="DarkRed"]**CC=mpicc**[/COLOR]
([COLOR="Blue"]http://www.mail-archive.com/r-help@stat.math.ethz.ch/msg94158.html[/COLOR])

greenlinux4r@greenlinux4r-desktop:~/R/i486-pc-linux-gnu-library/2.7$ CC=mpicc R CMD INSTALL --clean Rmpi_0.5-4.tar.gz
* Installing to library '/home/greenlinux4r/R/i486-pc-linux-gnu-library/2.7'
* Installing *source* package 'Rmpi' ...
[COLOR="DarkGreen"][B]checking for gcc... mpicc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
ERROR: configuration failed for package 'Rmpi'[/B][/COLOR]
** Removing '/home/greenlinux4r/R/i486-pc-linux-gnu-library/2.7/Rmpi'
** Restoring previous '/home/greenlinux4r/R/i486-pc-linux-gnu-library/2.7/Rmpi'

any help and comments will be appreciated.

---

