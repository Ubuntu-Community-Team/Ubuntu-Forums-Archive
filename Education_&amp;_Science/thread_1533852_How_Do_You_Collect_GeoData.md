---
title: "How Do You Collect GeoData?"
date: 2010-07-18
forum: Education &amp; Science
---

### Post by Herman on 2010-07-18
:D Hello everyone,
I'm using tangoGPS and I also have Quantum GIS.
I am using my EeePC for collecting map data, using some simple bash scripts I wrote for myself.

What I want to know is, how do other people do it?
Is there a program I don't know about yet that goes between a GPS and GIS for helping people collect mappable data? (For people who don't know how to write their own scripts)?

For example, a scientist is studying lizards, and catches one of a certain species and wants to record the GPS coordinates and input the measurements of the lizard and take down whatever other notes they need, relevant to the particular project they are working on.

What software would one use for something like that?

Or would it mean a lot of manual note taking on paper, or a lot of repetitious typing in a spreadsheet program or something similar?

Regards, Herman :D

---

### Post by Tattys on 2010-07-21
I know GPSBabel communicates GPS information with Quantum GIS. But I have never used it, so I am completely useless now. I'll be following along though since I am interested in GIS and Ubuntu.

---

### Post by Herman on 2010-07-21
:) Hello  Tattys' thank you for your reply, I was beginning to feel a little bit lonely here already.

I think I might have an idea. I'm looking at gnumeric spreadsheet.
Gnumeric is already one of my favorite programs for use with GIS data because we can 'save as' and choose '.csv' from gnumeric, and it makes a .csv file which is well suited to being loaded in Quantum GIS.

What I'm hoping to do is make a row of headings across the top of the page, with drop-down lists under them for a user to pick whatever choice they make out of a range of choices, which hopefully will later be able to be added to their map.

There are lots of other interesting looking possibilities in gnumeric which look like they might eventually be capable of being able to be used for what I want to do.
There is a toolbar for check boxes, radio buttons, pick lists, and so on, but I don't know yet so far how to get any of those to do anything. Maybe I'm 'barking up the wrong tree', (so to speak).

I'm surprised there isn't a program already for collecting GPS and associated data and converting it into a suitable format for importing into a map.
If there isn't one then I think we should start making something, even if it requires asking for help from somebody who knows how to write programs.

Making ones own collection of bash scripts is an interesting and educational passtime, but what happens if we're in a hurry, and we just want to get on with our data collecting as quickly and efficiently as possible? 

By the way, I'm not a scientist, I want to collect road data for engineers and I'm looking for an Open Source program for doing so.
All kinds of people these days have GPS.
How can we easily organize the information we gather with our GPSs coordinates and add it to our GIS data in an effective and efficient way?

Surely somebody knows or has some more ideas we can try to pursue? ...  :)

---

### Post by supermc on 2010-07-21
hi, 

i don't know what Quantum GIS. is, but hears how i do it.


have you heard of open street map.


some mapin programs are

josm

merkaartor

from the software center. 


you can use tango gps to log tracks on your eepc,

just click on the big i button on the top left.

srcoll trou the menu.

it will save the track to a folder on your home called maps. 


now to change this log to data that josm or merkaartor can use

we need a script.

i post it just after this. 

now you can download the area you need from open street map and change  and record anything u want, maybe even upload some stuff if you want, or just keep it on your computer, it's all good.

---

### Post by supermc on 2010-07-21
#!/usr/bin/perl
#
# (c) 2008 Marcus Bauer
# License: GPLv2
#
# Convert tangoGPS .csv logfiles into .osm files for processing in JOSM
#
# Usage: ./convert2osm.pl logfiles*.log
#
# creates for each input .log one .osm file
#




$curr_arg = "";

while(<>)
{

    if($curr_arg ne $ARGV)
    {
        if($curr_arg ne "")
        {
            &print_footer;
            close(FD);

            &convert2osm;

        }
        $curr_arg = $ARGV;

        $filename = $ARGV . ".gpx";
        print $filename . "\n";
        open(FD, "> $filename");
        &print_header;
    }

    else
    {
        &print_trackpoint;
    }
    
}


#--------------------------------
# and the same for the last file:
#--------------------------------
&print_footer;
&convert2osm;


### END MAIN


#########################################################
#
# sub routines
#
#########################################################


#---------
# header
#---------

sub print_header
{
print FD <<EOT
<?xml version="1.0" encoding="UTF-8"?>
<gpx    version="1.0"
    creator="convert2gpx.pl http://www.tangogps.org"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns="http://www.topografix.com/GPX/1/0"
    xsi:schemaLocation="http://www.topografix.com/GPX/1/0 http://www.topografix.com/GPX/1/0/gpx.xsd">

<trk>
<trkseg>

EOT
;
}


#-------------
# trackpoint
# ------------

sub print_trackpoint
{
@arr = split(',',$_);
chop @arr[6];


print FD <<EOT
<trkpt lat="@arr[0]" lon="@arr[1]">
  <ele>@arr[2]</ele>
  <speed>@arr[3]</speed>
  <course>@arr[4]</course>
  <fix>3d</fix>
  <hdop>@arr[5]</hdop>
  <time>@arr[6]</time>
</trkpt>

EOT
;
}


#---------
# footer
# --------

sub print_footer
{

print FD <<EOT

</trkseg>
</trk>
</gpx>

EOT
;

}


#=======================================================================
#
# convert 2 osm
#
#=======================================================================


#---------------------------------------------------------------------
#
# MAIN SUB convert to .osm
#
#----------------------------------------------------------------------
sub convert2osm
{

    #
    # 1. simplify with gpsbabel
    #
    `gpsbabel -i gpx -f $filename -x simplify,error=0.001k -x discard,hdop=3.1 -o csv -F $filename.csv`;


    #
    # 2. convert .csv to .osm
    #
    &convert_csv2osm;


    #
    # 3. remove .csv
    #
    `rm $filename.csv`;

}

# END MAIN SUB convert2osm




#----------------
# .csv to .osm
#----------------

sub convert_csv2osm
{

    print "converting to osm...\n";

    $i = 0;

    open(FDCSV,"$filename.csv") || die $filename.csv;
    open(FDOSM,"> $filename.osm") || die $filename.osm;

    &print_header_osm;

    while($_ = <FDCSV>)
    {
        &print_nodes_osm;
    }
    
    &print_way_osm;

    &print_footer_osm;

    close FDCSV;
    close FDOSM;

}


#----------
# header
#----------

sub print_header_osm
{
print FDOSM "<?xml version='1.0' encoding='UTF-8'?>\n";
print FDOSM "<osm version='0.5' generator='JOSM'>\n";
}



#---------
# nodes
#---------

sub print_nodes_osm
{
    $i--;

    @arr = split(',', $_);
    $lat = $arr[0];
    $lon = $arr[1];
    $lon =~ s/ //;
    print FDOSM "\t<node id='$i' visible='true' lat='$lat' lon='$lon' />\n";
}


#-------
# way
#-------

sub print_way_osm
{
    $way_id = $i - 1;

    print FDOSM "\t<way id='$way_id' action='modify' visible='true'>\n";

    $j = -1;
    for(; $i<0; $i++)
    {
        print FDOSM "\t\t<nd ref='$j' />\n";
        $j--;
    }

}


#----------
# footer
#----------

sub print_footer_osm
{
    print FDOSM "\t\t<tag k='highway' v='residential' /> \n";
    print FDOSM "\t\t<tag k='name' v='nn' /> \n";

    print FDOSM "\t</way> \n";
    print FDOSM "</osm> \n";
}

---

### Post by supermc on 2010-07-21
save the script as a txt file maybe with the name 

convert2osm.pl

make it exacute and put it in maps, 


then just cd to the map dir and to run type. 

./convert2osm.pl *.log


good luck, let me know if your need any more help, 

:popcorn:

---

### Post by mikero1959 on 2010-07-22
Hi,
 
I had been thinking about whether a similar program existed - for instance when I pick wild fruit or mushrooms from the countryside, it could be useful to capture geodata plus a few lines of text to describe the fruit etc, maybe add a photo.
 
I had been wondering if it would be difficult to code such a program for use on smartphones - in my case I would have been interested in a smartphone running the android OS.

---

### Post by supermc on 2010-07-22
well i guess you could just set up a constant log of the whole trip,

then take notes of the time that you found the shrooms and some details (yum yum) just as a txt file

then try to make a script that grabs the gps co-ords with the same time from your log and spits out 

some sort of data points that a mapin program can read, kind of like a point of interest

---

### Post by earlycj5 on 2010-07-22
> **Herman said:**
> :D Hello everyone,
I'm using tangoGPS and I also have Quantum GIS.
I am using my EeePC for collecting map data, using some simple bash scripts I wrote for myself.

What I want to know is, how do other people do it?
Is there a program I don't know about yet that goes between a GPS and GIS for helping people collect mappable data? (For people who don't know how to write their own scripts)?

For example, a scientist is studying lizards, and catches one of a certain species and wants to record the GPS coordinates and input the measurements of the lizard and take down whatever other notes they need, relevant to the particular project their are working on.

What software would one use for something like that?

Or would it mean a lot of manual note taking on paper, or a lot of repititious typing in a spreadsheet program or something similar?

Regards, Herman :D

The previously mentioned GPS Babel can read and write .csv files.  Those can easily be used in QGIS.
[http://www.gpsbabel.org/htmldoc-development/fmt_csv.html](http://www.gpsbabel.org/htmldoc-development/fmt_csv.html)


Looks like you can convert the log files to .gpx files using GPSBabel, I'd think you could use it to convert to .csv files as well.
[http://www.tangogps.org/gps/articles/9-Downloads.html#c213](http://www.tangogps.org/gps/articles/9-Downloads.html#c213)

---

### Post by Herman on 2010-07-22
> well i guess you could just set up a constant log of the whole trip,
then take notes of the time that you found the shrooms and some details  (yum yum) just as a txt file
then try to make a script that grabs the gps co-ords with the same time  from your log and spits out 
some sort of data points that a mapin program can read, kind of like a  point of interest:D Yes, exactly what I'm trying to think of.
I am dreaming of a program that can ask the user for details about a point of interest and record the information in a way that makes the information into a format able to be easily added to a map.

So, the user travels around and finds something interesting at a location, click an icon or presses a key and has the GPS coordinates recorded, then answers a series of questions regarding the size and shape of the object and all other relevant details, what color it is, and so on, whatever they need to know and records all that data. Then the user moves on until they find something else to record.

Ideally, when the user is in the field collecting data, the user shouldn't need to do very much typing, but where possible, just type 'y', or press a number from 1 to 10 or something like that, or click a drop-down menu to select an answer.

When the user gets home, or back to base, this information will be used for making the database behind the map, so in Quantum GIS, the user clicks on a point, (which is represented by an icon, with the information tool, and the information pops up all about the object that was found at that location.

For a doctor, maybe they want to record the geographic locations of some kind of disease outbreak. 
For a salesman, it might be locations where they sold various products, so they can see in their map the geographical areas where they have a good success rate.
For a biologist, the data being collected might be about the range and distribution of a species.

Here is a link to a Youtube about how to use the database in our Quantum GIS map, [QGIS  4 - Finding & Selecting Data]("http://www.google.com.au/url?sa=t&source=video&cd=1&ved=0CD0QtwIwAA&url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DZbnCrfoWnNk&ei=zqZITPaIDZDEvQP96IDBDg&usg=AFQjCNGckl__IwzqNpIjZ4v1NueADPHMyg&sig2=0DEkQqjU2Z6Mfc87-B_cTw")

What open source program can we use to gather the information about points of interest to put in our maps? Without needing to do a lot of laborious manual typing?

I am asking because I want open source to be the best and maybe we have a missing link in between our GPS programs and our map programs.

EDIT: PS, I saved your convert2osm.pl and I will try that out, supermc, thank you very much for that, it will be extremely useful to me to enable me to do something sightly different that I also wanted to be able to do. :)

---

### Post by Herman on 2011-02-25
:D The right-click --> 'POIs' --> 'add POI' menu in TangoGPS is great for the majority of users, who may be travellers or possiibly tourists.

I have discovered that the data that is thus collected is stored in an SQLite3 database file.

Quantum GIS can open SpatiaLite databases apparently, but not Sqlite3  database files, or at least I haven't learned how yet, so we need to  convert to a .csv file first.

It's possible to copy the .tangogps/poi.db file into some other directory and open it with SQLite Database Browser, then export it as a .csv file which can be opened with the delimited text plugin in Quantum GIS.

Wouldn't it be nice if there was a way that users could edit the 'add POI' category drop-downs and sub-categories to customize them to suit their various needs? 
Maybe some kind of companion program for tangogps that can be used to set up the database and configure the menus?

So instead of being restricted to 'car, cultural, medical ... ' and so on, a person can make up their own headings for features and attributes they need to have in their GIS.

I am quite well able to write my own bash scripts for my own data collection purposes, but I feel sorry for other users who might not have time or know how to do that, and I want Open Source to be the best! 

At the moment as far as I can tell there seems to be a void in between out Open Source GPS apps and our Open Source GIS apps and we just need a nice way to collect geodata and transfer it to our GISs.  :)

---

### Post by spinoza666 on 2011-02-26
Hey,

here's an idea:

You can use a smartphone with GPS functionality to collect data through forms. The data may either be viewed on the phone, or synced to an online database and viewed through GoogleEarth.

[http://www.epicollect.net/]("http://www.epicollect.net/") 

My idea is to move your data to a spatially enabled database of your own e.g. PostGIS, and then you do whatever you want with it in Quantum or GRASS GIS. Haven't tried it, but should be a breeze.

The good thing is that all of these apps are open-source as far as I am aware:) The bad thing is that you'd have to buy a fairly expensive phone.

---

### Post by Herman on 2011-02-26
:) Thank you, spinoza666, I have started to look into that and it looks like a very good answer, that's exactly the kind of thing I want to be able to do, (more easily than the way I do it now). 
I don't own any mobile phone at the moment. I will start looking at new Android phones to see if any are available in my area with with GPS and which might be able to do what you described. Thank you again, that's a very good lead. :)


I am still interested in more ideas and possible solutions if anyone else has an idea.

I am pleased to note that Quantum GIS now has its own Live GPS Tracking feature, new in version 1.6.0, at the moment I'm getting updates in the EeePC notebook I use with my USB-GPS receiver and I will start trying it out shortly. It seems to be a step in the right direction. :)

---

### Post by spinoza666 on 2011-02-27
Good to be of help:)

I got very interested in this myself, both for research and plain old fun, so I googled around a bit more.

There's a new phone coming out which is a collaboration between Garmin (the gps guys) and ASUS (the computer guys). Seems perfect for this kind of thing, although the downside is that it does not seem to have a keyboard. I don't own a Android phone myself, but I can imagine that the lack of a physical keyboard might be a pain in the *** if you're collecting a lot of data. The upside is that it is said to be very capable GPS compared to other phones with gps functionality. 

[http://garminfone.t-mobile.com/]("http://garminfone.t-mobile.com/")

It's called garminfone in the US, and nüvifone A50 in Europe by the way.

I also sent an email to the developers of epicollect to inquire about the possibility of syncing to your own local database (PostGIS), either directly from the phone or via their central online database. I will let you know when they get back to me.

---

### Post by Herman on 2011-02-27
> There's a new phone coming out which is a collaboration between Garmin  (the gps guys) and ASUS (the computer guys). Seems perfect for this kind  of thing, although the downside is that it does not seem to have a  keyboard. I don't own a Android phone myself, but I can imagine that the  lack of a physical keyboard might be a pain in the *** if you're  collecting a lot of data. The upside is that it is said to be very  capable GPS compared to other phones with gps functionality. 

[http://garminfone.t-mobile.com/](http://garminfone.t-mobile.com/):) Wow, that's great!

Yes, not having a keyboard is a bit of a pain, but most small handheld GPS devices have some kind of on-screen keyboard. Those can be a bit fiddly to use, but the compromise is worth it for many, especially when there are times the user needs to get out of the car and go walking, jogging or hiking across fields and through the bush, (woods) and so on. A small hand-held device is easier to carry than a laptop. Auto text completion can be a handy feature in those devices, and also the use of drop-down menus or pick lists to minimize the amount of typing required.
The other good thing about drop-down menus and pick lists are, they keep the data in the database nice and uniform, no spelling mistakes or typos which might interfere with the function of the database later on. :)

---

### Post by Herman on 2011-02-27
:D I tried out Quantum GIS's new Live GPS Tracking feature yesterday afternoon. 
It's use is explained in the          [FONT=Verdana][SIZE=2]      [QGIS User Guide]("http://download.osgeo.org/qgis/doc/manual/qgis-1.6.0_user_guide_en.pdf") for [/SIZE][/FONT]         [FONT=Verdana][SIZE=2]      [QGIS 1.6 'Copiapó' release]("http://qgis.org/component/content/article/114-qgis-16-copiapo-release.html") and there is also a web page I found about it too, [GPS Tracker tool in QGIS trunk - Linfiniti Geo Blog]("http://linfiniti.com/2010/01/gps-tracker-tool-in-qgis-trunk/").

Quantum GIS is a fully featured GIS application that can do almost anything, and it's great to have all that power under my fingertips. Qgis doesn't scale down quite as well as TangoGPS does for use in a small notebook PC like my EeePC, but it is still quite workable. I only needed to hold down the tab key and move the window around to gain access to buttons that were out of view on the screen a few times, and being a person who likes the normal Ubuntu in a notebook as opposed to the netbook edition, I'm used to that.

QGIS's new GPS tracking was a breeeze to use and it recognised my USB GPS receiver as soon as I plugged it in.

It did require a little manual typing for each entry when I tried it, I haven't had time to try it out enough to see if it has auto-completion or not. In any case it's great because it's quite easy to use and all the data goes directly into the database for the map. From there it is immediately transferable to Quantum GIS in my larger desktop main computer when I get home. No conversions from some file type to some other file type are necessary, no more work to do. 

I'm pretty excited about QGIS's new GPS tracker and I will be trying that out more in the next few days as time allows. It will suit most people's needs, especially those with a notebook PC or a laptop car computer. :)
[/SIZE][/FONT]

---

### Post by peterfernandes1 on 2011-03-01
Many parents and grandparents would like to start a coin collection for their children, but they don't know what to *collect*.
=============
peter

---

### Post by Herman on 2011-03-05
:) There's a punch line coming here sooner or later ...  :)

... or did I miss it ?

---

### Post by Herman on 2011-03-05
:D  I have marked this thread as 'solved'. I think spinoza666's answers will the GPS phones is a great idea especially for portabilty, (when hiking or bike riding etc).  

For a car computer I'm past trying out Quantum GIS's new Live GPS Tracking and I'm now using that all the time. It's great! The more I use it the better I like it. 
I was wrong when I said it doesn't scale well to the EeePC's small monitor. Since I took the time to organize things a little better I can now see more of the map window than I had before, there's no problem at all. 
A nice built-in safety feature is we can click 'Add feature' when we want to record a point and qgis stores the coordinates right away and I could move somewhere else to complete the form filling. That's important if you need to record a point where there could be safety reasons for not being able to remain there for very long. Form filling turned out to be a lot quicker than I thought too.
It's a job well done by the qgis team. Quantum GIS rocks!  :)

---

