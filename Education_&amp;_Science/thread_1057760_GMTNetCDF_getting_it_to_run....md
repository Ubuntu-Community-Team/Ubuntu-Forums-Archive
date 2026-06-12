---
title: "GMT/NetCDF getting it to run..."
date: 2009-02-02
forum: Education &amp; Science
---

### Post by valentijn on 2009-02-02
Hello out there,

I am having trouble running a script i downloaded to draw a geographical map of gene frequencies, on an example data file that was supplied with it... Probably this is because I did not properly set the path variables for GMT and NetCDF.

I included in my .bashrc file the following:

NETCDFHOME=/usr/lib
export NETCDFHOME
NETCDF_PREFIX=$NETCDFHOME
PATH=$PATH:/usr/lib/gmt/bin
GMTHOME=/usr/lib/gmt
export GMTHOME
MANPATH=$MANPATH:/usr/lib/gmt/man
export MANPATH

And stuff from the GMT Tutorial now works. But the shell script starting with the lines: 
____________________________________________________________________
# usage:  GMTPlotData.sh freqfile.txt

set XYZFile=$1

set W=-175   #-10
set E=180   #55
set S=-60    #25
set N=75    #73
set LowBound=0 # 0 for frequency data, u for likelihood data
set ContourInterval=$XYZFile.cpt #0.5
set AnnotationInterval=0
set Proj=m.025 #m.025  #w0/1:240000000 #m.025 #M6i #B100/45/20/30/6i

blockmean $XYZFile -R$W/$E/$S/$N -I3 | surface  -R$W/$E/$S/$N -G$XYZFile.grd -I.5 -T.7 -Ll0
______________________________________________________________________ 

on the example data file starting with the lines:

Ache_2003 56W 24S 0 1
Ainu_1996 142.45E 042.87N 0.02 1

Gives the following error messages (only the first part of error log shown):

valentijn@valentijn-desktop:~/Desktop$ ./GMTPlotData.sh DRB1-1501.txt
blockmean: Encountered first invalid record near/at line # 1
blockmean: Likely causes:
blockmean: (1) Invalid x and/or y values, i.e. NaNs or garbage in text strings.
blockmean: (2) Incorrect data type assumed if -J, -f are not set or set incorrectly.
blockmean: (3) The -: switch is implied but not set.
blockmean: (4) Input file in multiple segment format but the -M switch is not set.
blockmean: This file had 224 records with invalid x and/or y values


Is anyone able to help?
Thanks!

Valentijn
Institute of Biology
Leiden University

---

