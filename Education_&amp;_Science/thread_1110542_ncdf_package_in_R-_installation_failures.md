---
title: "ncdf package in R- installation failures"
date: 2009-03-29
forum: Education &amp; Science
---

### Post by kvk on 2009-03-29
I am unable to install the 'ncdf' package in R using the 

'install.packages("ncdf")' command from within R (in Emacs)

The return reads:

checking netcdf.h usability... no
checking netcdf.h presence... no
checking for netcdf.h... no
checking /usr/local/include/netcdf.h usability... no
checking /usr/local/include/netcdf.h presence... no
checking for /usr/local/include/netcdf.h... no
checking /usr/include/netcdf.h usability... no
checking /usr/include/netcdf.h presence... no
checking for /usr/include/netcdf.h... no
checking /home/arctos/include/netcdf.h usability... no
checking /home/arctos/include/netcdf.h presence... no
checking for /home/arctos/include/netcdf.h... no
checking /home/arctos/src/netcdf/netcdf.h usability... no
checking /home/arctos/src/netcdf/netcdf.h presence... no
checking for /home/arctos/src/netcdf/netcdf.h... no
checking /home/arctos/src/netcdf/netcdf-3.4/netcdf.h usability... no
checking /home/arctos/src/netcdf/netcdf-3.4/netcdf.h presence... no
checking for /home/arctos/src/netcdf/netcdf-3.4/netcdf.h... no
checking /home/arctos/src/netcdf/netcdf-3.4/src/libsrc/netcdf.h usability... no
checking /home/arctos/src/netcdf/netcdf-3.4/src/libsrc/netcdf.h presence... no
checking for /home/arctos/src/netcdf/netcdf-3.4/src/libsrc/netcdf.h... no
checking /sw/include/netcdf.h usability... no
checking /sw/include/netcdf.h presence... no
checking for /sw/include/netcdf.h... no
 
Fatal error: I cannot find the directory that holds the netcdf include file netcdf.h!
You can specify it as follows:
      ./configure --with-netcdf_incdir=directory_with_file_netcdf.h


However, downloading the .tar file and extracting all the files produces no 'netcdf.h' file anywhere. I've noticed that other folks have had issues with this installation as well. I also noticed that the 'ncdf' package isn't included in the Ubuntu repositories, perhaps for this very reason.

Any suggestions?

Thank you!!

kvk

---

### Post by Tibuda on 2009-03-30
You probably need to install the development headers package from your Ubuntu package manager. I'm not sure, but I guess it is netcdfg-dev

---

### Post by euler_fan on 2009-03-31
I haven't played with installs though EMACS . . . I usually do them after opening R with sudo in the terminal.

---

### Post by gunksta on 2009-03-31
It looks like R thinks it has already downloaded and installed this package. When you used R to install it, were you running as root? That's what it looks like it thinks happened.

This might be a good question for the r-project's mailing list.

---

### Post by kvk on 2009-03-31
Thanks for the input!

I'll see if I can make some headway. :)

---

### Post by Mamush on 2009-04-01
Did you install netcdf? it seems it is searching for the netcdf.h file. further information on installation of netcdf [http://www.unidata.ucar.edu/software/netcdf/](http://www.unidata.ucar.edu/software/netcdf/)

---

### Post by kvk on 2009-04-11
Yes- you folks were correct. Installing the general 'netcdf' library was needed before 'ncdf' would install correctly.

Thank you!

---

