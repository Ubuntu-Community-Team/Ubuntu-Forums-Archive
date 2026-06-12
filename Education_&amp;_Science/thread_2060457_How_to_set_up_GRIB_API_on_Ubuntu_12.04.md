---
title: "How to set up GRIB API on Ubuntu 12.04"
date: 2012-09-20
forum: Education &amp; Science
---

### Post by leeladam on 2012-09-20
I've been searching around a long time to make ECMWF's GRIB API work on my Ubuntu 12.04 and finally managed to set it up properly following the steps described in this tutorial.

[INDENT][INDENT]Version note 1: While working with Fortran 90 on 64-bit Ubuntu I kept on running into compiler problems like [_[COLOR="Blue"]this[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=1101434"). There is a GRIB API binary [_[COLOR="Blue"]available[/COLOR]_]("https://software.ecmwf.int/wiki/display/GRIB/Ubuntu+12.04+x86_64") for 64-bit Ubuntu, so the installation SHOULD work on all systems. However, I suggest that you use 32-bit version until compiler compatibility issues get solved.[/INDENT][/INDENT]

[INDENT][INDENT]Note 2: There is an uncertainty among Ubuntu distributions between /usr/include and /usr/local/include as default path for header and mod files. If a compiler asks for an included file or a header that you can find in any of these libraries, simply copying to the another one usually solves the problem. (The same issue with /usr/lib exists).   [/INDENT][/INDENT]



First, install the compilers you will need for your work. 

```

sudo apt-get update
sudo apt-get install gcc gfortran g++ build-essential

```

Then you have to download and install the [_[COLOR="blue"]Jasper[/COLOR]_]("http://www.ece.uvic.ca/~frodo/jasper/#download") package.


To install the GRIB API package (documentation provided [_[COLOR="Blue"]here[/COLOR]_]("http://pkgs.org/ubuntu-11.04/ubuntu-universe-i386/libgrib-api-dev_1.9.0-2_i386.deb.html")), type:

```
sudo apt-get install libgrib-api-dev
```


GRIB API is now installed on your system. To test your installation, download a Fortran 90 sample file from [[COLOR="blue"]_here_[/COLOR]]("https://software.ecmwf.int/wiki/display/GRIB/get_data.f90") and a GFS grib file from [[COLOR="Blue"]_here_[/COLOR]]("http://www.nco.ncep.noaa.gov/pmb/products/gfs/"). Modify the filename in the get_data.f90 code to the path of your grib file. Compile your code with linking the necessary libraries:

```
gfortran -c -I/usr/include get_data.f90 -o get_data.o  
gfortran get_data.o -L/usr/lib -lgrib_api_f90 -lgrib_api -o get_data.out
./get_data.out
```

You have to see the lat-lon-lev coordinates of all the grid points of your grib. Ctrl-C out of the script and start working with your gribs!

[INDENT][INDENT]Troubleshoot: if the compiler requires the grib_api.mod file or complains about undefined reference, check if the grib_api.mod file exists in your /usr/include folder and the libgrib_api_f90.so, libgrib_api.so files exist in your /usr/lib folder. If not, try to find them somewhere else on your computer (eg. in /usr/local/bin, /usr/local/lib) and link to that folder when compiling. If they can't be found on your computer then your installation may be wrong, try to reinstall the libgrib_api_dev package or make the tarred distribution through the steps explained [[COLOR="Blue"]_here_[/COLOR]]("https://software.ecmwf.int/wiki/display/GRIB/GRIB+API+installation"). [/INDENT][/INDENT]


You will probably need the g95 compiler that is used to make the GRIB API and other f90/95 files. It is NOT NECESSARY for the installation though as we used a deb package. You can get g95 from [[COLOR="blue"]_here_[/COLOR]]("http://www.g95.org/downloads.shtml").

The symbolic linking described in the docs of g95 didn't work for me. Simply copying the bin and lib libraries to your /bin and /lib folder will work fine (with renaming the binary to g95):

```
sudo cp /...your path to g95 unzipped folder.../g95-install/bin/*g95* /bin/g95
sudo cp -r /...your path to g95 unzipped folder.../g95-install/lib/* /lib 
```

You can check your installation with calling the compiler without arguments. You have to see this:

```
user@ubuntu:~$ g95
g95: no input files
```

---

### Post by TeteAUbunter on 2012-10-16
Hi,
Many thanks leeladam for this tutorial. It helped me a lot and prevented headaches.

Before installing the GRIB_api package, I installed dependencies with:
```
sudo apt-get build-dep libgrib-api-dev
```In my case, I needed the pygrib install afterwards. 
I post below the steps I followed (just in case it could help). One can also refer to [http://pygrib.googlecode.com/svn/trunk/docs/index.html](http://pygrib.googlecode.com/svn/trunk/docs/index.html).
 #3.Install python modules
 #install numpy
```
sudo apt-get install python-numpy
``` #install pyproj
```
sudo apt-get install python-pyproj
``` #4.Install pygrib
 #Need Python development header
```
sudo apt-get install python2.7-dev
``` #Download pygrib-1.9.5.tar.gz at [http://code.google.com/p/pygrib/downloads/list](http://code.google.com/p/pygrib/downloads/list)

#Copy setup.cfg.template to setup.cfg, edit the file
#remove "#" from "#grib_api_dir = /usr/local"
#remove "#" from "#jasper_dir = /usr/local"
#remove "#" from "#png_dir = /usr"
#remove "#" from "#zlib_dir = /usr"
#save
```
cd ~/pygrib-1.9.5
python setup.py build
sudo python setup.py install
```Successfully installed in my case!

Best,
TeteAUbunter

---

