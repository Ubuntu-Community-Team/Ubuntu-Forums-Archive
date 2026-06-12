---
title: "HOWTO:  PostGIS on Fiesty i386"
date: 2007-08-19
forum: Education &amp; Science
---

### Post by zedmaster on 2007-08-19
Hey guys!  I've been struggling with an installation of UbuntuGIS for ages now.  The UbuntuGIS wiki would have us believe you merely need to install the packages.  Most of the directions the wiki points to are for older versions of Ubuntu, other versions of Linux, older versions of the packages, and (yippie) building from source.  I had all kinds of fun trying to trudge through this one.  Anyway, just now, I was able to get it all running, and import a shapefile into PostGIS.  This is like an alpha HOWTO that I wanted to share with you all.  

Couple points:  I'm not an expert on GIS, or Linux.  If you feel that I could have written the commands more simply, or totally missed touching on some important points, PLEASE tell me so I can improve it.  If you have other thoughts, PLEASE tell me.  I want your thoughts!  Finally, please forgive me document formating, as I just whipped this up.

> **HOWTO:  Install Postgresql and PostGIS on Fiesty 7.04**

This was done on a fresh install of Fiesty 32-bit i386 version, it is possible that these instructions apply to other distributions, but do NOT assume that.  I am new to GIS on Linux, so hopefully this HOWTO will be helpful for other newbies. 

POSTGIS and posgresql are basically going to work hand in hand on your GIS workstation.  Basically postgresql is a type of SQL database.  It may not be especially important to have a deep understanding of postgresql to run GIS, as long as you can get it to run.  If you want to know more, check out postgresql.org.  I've used version 8.1 of postgresql, this is not the latest version, but it is the UbuntuGIS spec.  DO NOT install version 8.0, as there are major differences.  You would probably have good luck using 8.2, but that's outside the scope of this document.  

The actual package for postgis is called 'postgis.'  There is also a package that spatially enables the postgresql server called postgresql-8.1-postgis.

[B]Step One: Install the Packages
[/B]
Open a command line and type the following:

*sudo apt-get install postgresql-8.1 postgis postgresql-8.1-postgis*

All of these should install just fine on a stock Ubuntu Fiesty 7.04 i386 system.

**Step Two:  Configuration**

Installing postgresql from the packages means that most of the configuration is already done.  It makes a database cluster, and takes care of all the environment variables.  Usually it does this quite well.  Unfortunately, most of the directions that the UbuntuGIS page point you to are for people building from source.  I'm a busy guy, and I don't really feel a need to build from source when there is a handy package right there.  If you run into trouble, the documentation at postgresql.org could come in handy, but actually added a lot of confusion in my own case.

NOTE:  if you installed postgresql-8.1 from the package, there is already a user called postgres.  Many howtos instruct you to create this user, but there is no need.

At this point you need to use a postgresql utility called psql to change the password the postgres user needs for access to this database:

*sudo -u postgres psql template1*

("template1" is a generic database postgresql uses as a basis to spawn new databases, there is really no reason to have a deep understanding of it for GIS)

the psql utility will now load its own text prompt.  Do not be alarmed.  Now enter this command (replace XXXXXXXX with your own password).

*ALTER USER postgres WITH PASSWORD 'XXXXXXXX';*

Quit psql:

*\q*

Now you'll need to create a database.  This should be very easy, just remember to use the postgres user (sudo -u postgres) to execute the command, or you'll have permissions problems up the wazzoo.  

*sudo -u postgres createdb mydb*

If all goes well it will say "CREATE DATABASE," if all does not, you probably aren't using the distributions intended for this howto.  I wish you luck, but I can't help with that.

"mydb" is the name of our test database.  Feel free to name it whatever you like.  You now have a postgresql database!  Congrats!  That's pretty much it for postgresql!

**Step Three: More Configuration**

There are a few things you'll have to do to get POSTGIS to "spatially enable" your database.  

First, you set up the postgis libs:

*createlang plpgsql mydb*

Then import the sql files to your database:

[I]sudo -u postgres psql -d mydb -f usr/share/postgresql-8.1-postgis/lwpostgis.sql

sudo -u postgres psql -d mydb -f usr/share/postgresql-8.1-postgis/spatial_ref_sys.sql[/I]

Note: One of the most common problems in this setup is the location of the above files.  If you built from source, are using different package versions, or are using a different version of ubuntu, you may find that these files don't exist at that location.  They are probably around somewhere, but I can't help with that.

**Step Four: Import a Shapefile to PostGIS**

Now for some real excitement.  We're going to import an ESRI type shapefile into postGIS.  This can get a little iffy, and I know I could have written this command more simply, but it DOES work under the conditions specified for this howto.  

*sudo -u postgres shp2pgsql -D SHAPEFILE mytable mydb | sudo -u postgres psql mydb*

You'll need to replace "SHAPEFILE" with the name and location of your shapefile.  You can generally leave "mytable" as it is.  "mydb" is, of course, your database.  The most common problem here is making a typo on your file location.

Double Congratulations!  You've just imported a shapefile into a postgis, spatially enabled database!!!   That is a big step.



Thanks for reading it!  I really hope that helps someone.  Again, get back to me with comments and suggestions!

Matthew

---

### Post by earlycj5 on 2007-08-20
The PostGIS wiki also has a how-to for Ubuntu and RPM based systems as well.

[http://postgis.refractions.net/support/wiki/index.php?PostgisOnUbuntu](http://postgis.refractions.net/support/wiki/index.php?PostgisOnUbuntu)

I've used it in the past to get it set up.

---

### Post by GingerAlex on 2007-08-29
thanks to zedmaster that got me up and running -

although I'd have thought the PostGIS stuff was slightly advanced for a 'get you started' or am I just behind the times? 

cheers,
Al

---

### Post by Go_Bucks on 2007-10-03
I can't get past "createlang plpgsql mydb" as it tells me I need to be superuser. I tried the same with sudo and it didn't work either. I am stuck. Following the instructions on the PostGIS website theoretically set it up fine with no errors, but all of my gis programs tell me that postgis is not enabled when I connect to the database. 

HELP

---

### Post by groef on 2007-10-28
Need to run the following command (My database is testdb, in examples it is mydb)
* sudo -u postgres createlang plpgsql testdb*

It worked for me.

Installation: Ubuntu 7.04 Feisty Fawn
Postgres 8.2
PostGIS: 1.3.1 installed from source

Great help document Matthew!! Exccellent

---

