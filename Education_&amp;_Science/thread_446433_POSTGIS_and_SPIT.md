---
title: "POSTGIS and SPIT"
date: 2007-05-16
forum: Education &amp; Science
---

### Post by zedmaster on 2007-05-16
I've been working on installing the packages as described on the UbuntuGIS wiki.  It would appear I've gotten that all squared away.  The problem I'm running into is that SPIT, the tool for converting shapefiles to POSTGIS isn't working and it won't give me any clues.  SPIT starts up, it connects to my postgresql server, and it lets me pick which files I want to import to POSTGIS.  When I actually click import, it says "Problem inserting features from file: media/sda7/... etc... etc..."  Well it didn't actually say etc.. etc...  That was me.  No other clues as to what's going on.  I've tried running as my normal user, as the postgres user, and under SUDO.  No luck.  My feeling is that this may relate to permissions, but then why wouldn't SUDO work?  

Does anybody have any clues here?  I'm tearing my hair out, and that's hard because I don't have any.


[I]
Much love to the Linux...[/I]

Matthew

---

### Post by timmie on 2007-05-20
I am a starter in postgis my self. But for the 1rst time I found it easy to use the QGIS plugin to import a shape into POSTGIS


For more updated packages you may also see this:
[http://permalink.gmane.org/gmane.comp.gis.freegis/2103](http://permalink.gmane.org/gmane.comp.gis.freegis/2103)

Regards!

---

### Post by earlycj5 on 2007-05-21
> **zedmaster said:**
> I've been working on installing the packages as described on the UbuntuGIS wiki.  It would appear I've gotten that all squared away.  The problem I'm running into is that SPIT, the tool for converting shapefiles to POSTGIS isn't working and it won't give me any clues.  SPIT starts up, it connects to my postgresql server, and it lets me pick which files I want to import to POSTGIS.  When I actually click import, it says "Problem inserting features from file: media/sda7/... etc... etc..."  Well it didn't actually say etc.. etc...  That was me.  No other clues as to what's going on.  I've tried running as my normal user, as the postgres user, and under SUDO.  No luck.  My feeling is that this may relate to permissions, but then why wouldn't SUDO work?  

Does anybody have any clues here?  I'm tearing my hair out, and that's hard because I don't have any.


[I]
Much love to the Linux...[/I]

Matthew

Matthew, I've run into much the same problem, but usually only with .shp files I've created from X,Y data in a .csv file using QGIS to save a .shp file.

In those cases I use shp2pgsql and import the .shp file into my Postgis dbase that way.  Then if need be, and usually it needs to be done, I change the column types around so I have numeric or text rather than ints so that I can use the data with QGIS and GRASS.

I was able to use SPIT to import other .shp files that I downloaded, just not any that I created by creating them in QGIS.  My regular login has permissions to the database I'm using for this project.

If it is a permissions issue, please let me know.  If you need more help, let me know.  I know I was trying to tear my hair out too, and all I have is my mustache, we're in the same boat.  :p

Timmie, SPIT is exactly what you're talking about here.  That is what's not working.

---

### Post by timmie on 2007-05-22
> **earlycj5 said:**
> Timmie, SPIT is exactly what you're talking about here.  That is what's not working.

I just tested it here. It worked well. Worked after I reinstalled postgres/gis since something wasn't well set up here. I just took the time and set it up again and it let mit import and display data from my home directory.

Please try to save your data on a unix file system like
/tmp, /var/gis or ~

You seem to use a vfat USB drive or something. Maybe it's related to that. There's also a very helpful file

/usr/share/doc/postgresql-8.1-postgis/README.Debian.gz

Where you can find information on how to enable postgis!

Good luck!

---

### Post by earlycj5 on 2007-05-22
> **timmie said:**
> I just tested it here. It worked well. Worked after I reinstalled postgres/gis since something wasn't well set up here. I just took the time and set it up again and it let mit import and display data from my home directory.

Please try to save your data on a unix file system like
/tmp, /var/gis or ~

You seem to use a vfat USB drive or something. Maybe it's related to that. There's also a very helpful file

/usr/share/doc/postgresql-8.1-postgis/README.Debian.gz

Where you can find information on how to enable postgis!

Good luck!

Like I said, it worked for me with some files, not with others.

It had nothing to do with a USB disk either.  They were in my /home/user/GIS directory.

Cheers!

---

### Post by handaxe on 2007-06-13
@earlycj5: thanks for this - I met the problem and, as the majority of my shape files are Qgis generated via xyz stuff, it was a miserable experience. 

You saved me some (much needed) hair.......

BTW: has this been filed as a bug against Qgis (I would guess thats the "culprit")?


HA

---

### Post by timmie on 2007-06-14
Hello,
I did have very good experience creating a point shape from DBF with SAGA GIS
[LIST]
[*][http://www.saga-gis.uni-goettingen.de/html/index.php](http://www.saga-gis.uni-goettingen.de/html/index.php)
[*][http://sourceforge.net/forum/forum.php?forum_id=703386](http://sourceforge.net/forum/forum.php?forum_id=703386)
[/LIST]

The created dbf is not spacially referenced, through (no project file).

I used the binary packages successfully under linux.

Hope that helps.

---

