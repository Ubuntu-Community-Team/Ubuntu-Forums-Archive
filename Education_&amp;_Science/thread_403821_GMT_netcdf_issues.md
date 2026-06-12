---
title: "GMT netcdf issues"
date: 2007-04-07
forum: Education &amp; Science
---

### Post by vortmax on 2007-04-07
I'm attempting to install GMT (Generic Mapping Tools) on a Dapper install.

I used the download/install script from their page which includes automatic installation of the netcdf libraries.  It wound up installing the netcdf libs to my home directory and then instructed me to set the variable NETCDFHOME to my home directory.  So I moved the netcdf folder to /usr/local and set NETCDFHOME=/usr/local

When I try and run any of the GMT scripts, I get this error:

```

pscoast: error while loading shared libraries: libnetcdf.so.4: cannot open shared object file: No such file or directory

```

I've checked and that library is in the netcdf folder which the NETCDFHOME variable is pointing to. Is there something I'm missing here?

---

### Post by kleeman on 2007-04-08
The program is not finding the netcdf libraries. I looked at the website for GMT and there seems to be a heavily automated install option using an already installed netcdf 3.6. Why not use this and install the netcdf that is in the universe repository.

---

### Post by ehowell on 2007-06-29
I know that this is old but I just got this error myself.

The problem was that I was not able to see the library under my local install directory for NetCDF (/usr/local/GMT/netcdf-3.6.2/lib)

so I made a symbolic link from that directory to /usr/lib

ln -s  /usr/local/GMT/netcdf-3.6.2/lib/libnetcdf.so.4 /usr/lib/libnetcdf.so.4

---

