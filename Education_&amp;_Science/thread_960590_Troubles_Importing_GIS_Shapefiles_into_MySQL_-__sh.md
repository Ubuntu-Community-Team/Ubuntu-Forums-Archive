---
title: "Troubles Importing GIS Shapefiles into MySQL -  shp2mysql"
date: 2008-10-27
forum: Education &amp; Science
---

### Post by Grandma_DOG on 2008-10-27
For database folks trying to get GIS shapefiles into MySQL, there seems to be few options. Most of those options are homegrown.

First is shp2mysql, the equivalent of shp2psql for postgis. Found at [http://kartoweb.itc.nl/RIMapper/]("http://kartoweb.itc.nl/RIMapper/")

It, however, has to be built from source and all you have to do is run 'make' but on my 64bit system, it pukes out-

"a:~/junk/src$ make
cc  shpopen.o dbfopen.o getopt.o shp2mysql.o    -o shp2mysql 
shpopen.o: file not recognized: File format not recognized
collect2: ld returned 1 exit status
make: *** [shp2mysql] Error 1"

So no frickin clue what that means, only it doesn't work.

The second option is another version of the same file but installed in the package mapserver-bin

sudo apt-get install mapserver-bin
and you get a clean install

but entering 'shp2mysql' and it pukes:
"Can't locate Geo/Shapelib.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/bin/shp2mysql line 9.
BEGIN failed--compilation aborted at /usr/bin/shp2mysql line 9."

Again, its broken for everyone who's not a programmer.  Research hints that some Shapelib written in perl is needed.

Then there is libmygis.  Found at: [http://jcole.us/software/libmygis/]("http://jcole.us/software/libmygis/")

./configure works
make coughs up some puke and crashes.


So does anyone know a tool to load Shapefiles into mysql?  That WORKS?!?

---

### Post by thundercat78 on 2009-06-18
try using ogr2ogr
for more information , click here:
[http://www.bostongis.com/PrinterFriendly.aspx?content_name=ogr_cheatsheet](http://www.bostongis.com/PrinterFriendly.aspx?content_name=ogr_cheatsheet)

---

### Post by thundercat78 on 2009-06-18
this is another blog explaining on how to load shapefile into mysql.
[http://blog.thematicmapping.org/2008/03/loading-spatial-data-into-mysql.html](http://blog.thematicmapping.org/2008/03/loading-spatial-data-into-mysql.html)

---

### Post by warthog10 on 2009-07-02
maybe try running the shapefile in grass gis and then exporting into MySql.

[http://grass.itc.it/grass64/manuals/html64_user/db.out.ogr.html](http://grass.itc.it/grass64/manuals/html64_user/db.out.ogr.html)

---

