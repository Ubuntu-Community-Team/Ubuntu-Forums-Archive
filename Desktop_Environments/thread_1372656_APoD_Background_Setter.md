---
title: "APoD Background Setter"
date: 2010-01-04
forum: Desktop Environments
---

### Post by o1911 on 2010-01-04
Hi there,

After spending a couple of weeks tinkering (and simultaneously learning bash) with the script found [here]("http://ubuntuforums.org/showthread.php?p=4213525#post4213525") (the second script, and many thanks to the authors), I can now enjoy the "Astronomy Picture of the Day" (APoD) as my wallpaper fetched daily with zero effort.  I thought it would be nice to share with other interested people out there.

The APoD website is [here]("http://antwrp.gsfc.nasa.gov/apod/astropix.html") if you would like to see what it's all about.

If you would like this script setup on your system, follow these steps:


1) Download the script I've helped modify.  Save it anywhere you like and call it whatever you want, just remember where it is.  I've called mine apodwallpaper and by default it saves the APoD pictures to ~/Pictures/APoD/, although this is easily changed.

```
#!/bin/bash
#Filename: apodwallpaper
#Purposes: Downloads NASA Astronomy Picture of the Day and displays it as the GNOME background 
#Author(s): acvwJosh of Ubuntu Forums, modified by Colin Dean <http://cad.cx>, o1911

# change this if you want the image to be in a different directory
DIRECTORY=$HOME/Pictures/APoD
cd $DIRECTORY

# fetch the apod site's text, to determine the latest apod
SITE=http://apod.nasa.gov/apod/index.html

if $(wget $SITE); then
	# the prefix of the filename is to be the current date
	FILENAME=$(cat $(echo $SITE | rev | cut -d "/" -f -1 | rev) | grep $(date +%Y) | head -1)

	# format this date to have underscores instead of spaces
	FILENAME=$(echo $FILENAME | tr " " "_")
	
	# check if today's file exists
	if [ ! -f $FILENAME* ]; then
		# if not, download image from apod site
		wget -A.jpg,.JPG -R.txt -r -l1 --no-parent -nH $SITE

		# find largest file (biggest res. picture)
		BIGFILESIZE=$(find apod/ -printf '%s\n' | sort -nr | head -1)
		
		# check if biggest file is a dir (no picture today)
		if [ $BIGFILESIZE == 4096 ]; then
		## there is no picture for today
			# set today's picture to be yesterday's
			YESTERDAY=$(( $(date +%s) - 86400 )) # 86400 seconds in a day
			ln -sf "$(find $DIRECTORY/ | grep -i $(date -d "@$YESTERDAY" +%Y_%B_%d))" "$HOME/wallpaper"
			
			## set today's picture to be a random one
			#NUMBEROFFILES=$(find . | wc -l)
			#NUMBER=$(( $RANDOM % $NUMBEROFFILES ))
			#ln -sf "$DIRECTORY/$(ls | tail -$NUMBEROFFILES | head -$NUMBER | tail -1)" $HOME/wallpaper
			
			rm -rf ap* *.apod robots.txt* index.html*
			exit 0
		fi
		
		## we have a picture for today
		# get its relative path for movement to ${DIRECTORY}
		BIGGESTFILE=$(find apod/ -size ${BIGFILESIZE}c)
		# also get its base filename to append
		BIGGESTFILENAME=$(find apod/ -size ${BIGFILESIZE}c -printf '%f\n')
		# declare our final filename for today's picture
		WALLPAPER=$FILENAME-$BIGGESTFILENAME
		# move it to the proposed directory
		mv $BIGGESTFILE $DIRECTORY/$WALLPAPER
	else
		WALLPAPER=$(find $DIRECTORY/ -name $FILENAME* -printf "%f\n")
	fi
else # wget failed. internet up?
	exit 1
fi

# as cron cannot set the wallpaper on its own, use a symbolic link to be a pointer to the background
rm $HOME/wallpaper
ln -sf "$DIRECTORY/$WALLPAPER" $HOME/wallpaper

# get rid of cruft
rm -rf ap* *.apod robots.txt* index.html*
exit 0

```

2) Setup your crontab to make this script run automatically.  You can edit your crontab with the command "crontab -e".  If you are unfamiliar with text-editors, nano will be the easiest to use.  More about crontab [here]("https://help.ubuntu.com/community/CronHowto").  To give a clue as how your crontab should look, this is what calls my apod script:

```
# m h  dom mon dow   command
*/30 * * * * /home/username/bin/apodwallpaper

```

3) Get your GNOME session to use the wallpaper as your background- do the usual right-click desktop, change desktop background, add, and point to the 'wallpaper' file in your home ($HOME) directory.  Everytime cron runs apodwallpaper and downloads a new picture, your desktop will now automatically update to it.

The reason I've my script called at many times in the day is just so I might still get the picture if my computer is off for a period there.  I've made the script so that it won't redownload the picture every time so calling it many times is not a problem.

Hopefully that's enough to get most people setup.  If you can think of how to make this script even better, please say so or even do so and post back here.  Cheers!

edit:  script wasn't working... fixed now.
edit again:  made the script much better; now there is no dependence on your local timezone.

---

### Post by vinx on 2010-01-10
Why not get the picture-of-the-day of National Geographic? I was sooo tired of APOD, so I altered some script. ;)

```
#!/bin/sh
#Based on code of APOD, you can really find everywhere on the web.

#Downloading html of the Picture-Of-The-Day
wget -N http://photography.nationalgeographic.com/photography/photo-of-the-day/ -O /tmp/ngpod.html

#Getting the URL of the image
img_location=`egrep -o "http://[^<]*1600x1200[^>]*\.jpg" /tmp/ngpod.html`

rm /tmp/ngpod.html

#Download image
TODAY=$(date +'%Y%m%d')
wget $img_location -O ~/Afbeeldingen/ngpod/$TODAY.jpg

# Setting background-image.
# NB: Use an absolute URL
gconftool-2 -t string -s /desktop/gnome/background/picture_filename "/home/vincent/Afbeeldingen/ngpod/$TODAY.jpg"
gconftool-2 -t string -s /desktop/gnome/background/picture_options "zoom"
# Possible values are "none", "wallpaper" (eg tiled), "centered", "scaled", "stretched", "zoom"

```

Just run this script whenever you don't like the previous anymore. Check out [http://photography.nationalgeographic.com/photography/photo-of-the-day/](http://photography.nationalgeographic.com/photography/photo-of-the-day/) for more info and to see what you've missed.

---

### Post by sierraindigo on 2010-04-25
> **o1911 said:**
> Hi there,

After spending a couple of weeks tinkering 
...
edit:  script wasn't working... fixed now.
edit again:  made the script much better; now there is no dependence on your local timezone.

fantastic script and thank you for sharing it.
however, i would really love to have the text description for the picture too in the same way as [this]("http://nightskylive.net/software/apod/screenshot1.jpg") from [here]("http://nightskylive.net/software/apod/"). if you're able to amend the script to do that as well or give me some pointers to how to do it myself (only very basic skills at moment...) i'd be incredibly grateful. ta.

---

### Post by nvsbl on 2010-06-13
> **sierraindigo said:**
> fantastic script and thank you for sharing it.
however, i would really love to have the text description for the picture too in the same way as [this]("http://nightskylive.net/software/apod/screenshot1.jpg") from [here]("http://nightskylive.net/software/apod/"). if you're able to amend the script to do that as well or give me some pointers to how to do it myself (only very basic skills at moment...) i'd be incredibly grateful. ta.

A very rough outline of a proper APoD plugin.

This is probably the first piece of software I've shared with anyone. Bear with me.

I'm trying to get Launchpad set up so I can share this code, but, like I said, I'm quite new to this. Anyone interested in this project who might want to help me would be greatly appreciated.

1. Today's Astronomy Picture of the Day.
2. One large toggle button. When clicked, hides, explanation and button label changes to "Show". I intend to make it small, square and translucent.
3. Title of photo. Currently reads 'None" because my method of extracting this info from the APoD page isn't very exact. It worked yesterday. Will probably work later today.
4. Explanation. Notice the poor formatting. I'm such a n00b I can't overcome this.
5. Today's date.

As of now, it simply downloads the APoD daily page, and extracts the relevant information from that.
I'm working on storing this information in Desktop Couch, formatting the paragraph and improving the visibility of the text with a background color, and a bunch of other things. I'm pretty new to this, so everyone should take a look at the code and add you're suggestions/improvements/whathaveyou.

```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
#
# This file is part of the APoD Desktop Art and Description plug-in
#
# Kopimi c2010 James Martin < nvsbl.monstr at gmail dot com >
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.
#
#
# APoD DESKTOP DESCRIPTION WIDGET
# A program to print the Astronomy Picture of the Day
# description in a widget, along with the picture as
# the desktop background. This widget will be collapsable,
# functioning exactly as the Windows 7 APoD background changer does.
#
# Will also function as commandline apod-description-getter, 
# which will then be used for my .zshrc file instead of that stupid
# WoW calendar someone packed in with it.
#

# get page
# find paragraph
# put paragraph, link and picture in DesktopCouch
# print to desktop with cairo
# 

import urllib
import re
import datetime
import pygtk
pygtk.require('2.0')
import gtk
import cairo
import glob

from desktopcouch.records.server import CouchDatabase
from desktopcouch.records.record import Record

global MONTHS
MONTHS = ("January",
          "February",
          "March",
          "April",
          "May",
          "June",
          "July",
          "August",
          "September",
          "October",
          "November",
          "December")

global title
global descrip
global date

global IMGDR
IMGDIR = "/home/nvsbl/Pictures/wallpaper/APoD/"
APOD = "http://antwrp.gsfc.nasa.gov/apod/astropix.html"

# Transparent window with cairo
def transparent_expose(widget, event):
    """Make the given widget transparent."""
    cr = widget.window.cairo_create()
    cr.set_operator(cairo.OPERATOR_CLEAR)
    region = gtk.gdk.region_rectangle(event.area)
    cr.region(region)
    cr.fill()
    return False

class DesktopWindow(gtk.Window):
    """A transparent and borderless window, fixed to desktop."""
    def __init__(self, *args):
        gtk.Window.__init__(self, *args)
        
        self.set_type_hint(gtk.gdk.WINDOW_TYPE_HINT_DOCK)
        self.set_keep_below(True)
        self.set_decorated(False)
        self.stick()
        
        screen = self.get_screen()
        rgba = screen.get_rgba_colormap()
        self.set_colormap(rgba)
        self.set_app_paintable(True)
        self.connect("expose-event", transparent_expose)

global toggle
toggle = True
        
class DescriptionWidget:
    global title
    global descrip
    global date
    
    """"Widget with actual description in it."""
    def callback(self, widget, data=None):
        global toggle
        if toggle:
            self.label.hide()
            self.button.set_label("Show")
            toggle = False
            print "Hiding information."
        else:
            self.label.show()
            self.button.set_label("Hide")
            toggle = True
            print "Showing information."
        
    def __init__(self):
        self.window = DesktopWindow()
        self.window.move(20,50)
        self.window.set_default_size(500,500)
        
        self.window.connect("destroy", lambda wid: gtk.main_quit())
        self.window.connect("delete_event", lambda a1,a2:gtk.main_quit())
        
        self.box = gtk.VBox()
        self.window.add(self.box)
        
        self.label = gtk.Label()

        self.button = gtk.Button(label='Hide')
        self.button.set_focus_on_click(False)
        focus = self.button.get_focus_on_click()
        if focus:
            print "Focus on click:\tTrue"
        else:
            print "Focus on click:\tFalse"
        self.button.connect("clicked", self.callback, "hide info")
                
        self.box.pack_start(self.button, expand=False, fill=False)
        print "Packing button"
        self.box.pack_start(self.label, expand=True, fill=True)
        print "Packing label"
        
        self.label.set_markup("""<span foreground='#ffffff'><b>%s</b>\n<b>Explanation</b>: %s\n<i>%s</i></span>""" % (title, descrip,date,));
        
        self.window.show_all()
        print "Showing everything."
        
        
def get_page(url=APOD):
    """Opens page"""
    print "Getting page %s" % url
    return urllib.urlopen(url).read()

def month2num(month):
    """Takes a given month and converts it to the appropriate number."""
    x = 0
    while x < len(MONTHS):
        if month == MONTHS[x]:
            return x + 1
        x = x + 1
    return False

def num2month(num):
    """Takes a given number and converts it to a month."""
    if str(type(num)) == "<type 'int'>":
        return MONTHS[num-1]
    
    
def is_today(date):
    """Takes a date and determines whether that date is today's.
    Date accepted in form YYYY Month DD"""
    today = datetime.date.today()
    if date == today:
        return True
    else:
        return False

def d2str(date):
    year = str(date.year)
    month = num2month(date.month)
    day = str(date.day)
    
    return year + " " + month + " " + day

def get_title(page=None):
    print page.split("""alt="See Explanation.
Moving the cursor over the image will bring up an annotated version.
Clicking on the image will bring up the highest resolution version
available."></a> 
</center> """)

def get_date(page):
    """Finds date on page
    f=format. d = datetime object, str = string"""
    
    date_pattern = "\d+\s[a-zA-Z]+\s\d+"
    p = re.compile(date_pattern)
    q = p.search(page)
    start = q.start()
    end = q.end()
    date = page[start:end]
    sdate = date.split(" ")
    
    year = int(sdate[0])
    month = int(month2num(sdate[1]))
    day = int(sdate[2])
    
    return datetime.date(year,month,day)
        
    
def get_descrip(page):
    strip_before_junk = page.split("<b> Explanation: </b>")[1].strip()    
    strip_after_junk = strip_before_junk.split("<p> <center>")[0].strip()
    return strip_after_junk

def todays_img_exists():
    todaystr = get_todaystr()
    filelist = glob.glob(IMGDIR + '/*.jpg')
    date = todaystr.split(' ')
    month = num2month(date[0])
    year = str(date[1])
    day = str(date[2])
    newdatestr = year + "_" + month + "_" + day
    for f in filelist:
        if f.find(newdatestr):
            pass
    
# Desktop couch stuff
def get_todaystr():
    today = datetime.date.today()
    month = str(today.month)
    if len(month) == 1:
        month = '0' + month
    year = str(today.year)
    day = str(today.day)
    if len(day) == 1:
        day = '0' + day
    return month + " " + year + " " + day
    
def update_couchdb():
    
            
    
    db = CouchDatabase("apodbackgroundchanger", create=True)
    record_type = "somerecord.html"
    #new_record = Record("date" : todaystr,
#                        "description" : descrip,
#                        "image" : }, record_type)
    #new_record.attach(

def record_exists(db, record_type):
    todaystr = get_todaystr()
    results = db.get_records(record_type = record_type, create_view=True)
    for records in results:
        record = records.value
        if record["date"] == todaystr:
            return True
        else:
            return False

def main():
    global descrip
    global date
    global title
#    update_couchdb()
    page = get_page(APOD)
    date = datetime.date.today()
    print "Getting date: %s\n" % date
    if is_today(date):
        date = get_date(page)
        title = get_title(page)
        print "Getting title: %s\n" % title
        descrip = get_descrip(page)
        print "Getting descrip: %s\n" % descrip

        instance = DescriptionWidget()
        gtk.main()
    
if __name__ == "__main__":
    main()
    
```

edit: My code is very sloppy. I'm sorry about that.

---

### Post by nvsbl on 2010-06-15
UPDATE June 15 2010:

Thus far, this is what I've accomplished:

When this script first gets the relevant information, it writes it to a Desktop Couch DB. Subsequent calls to the script during that day will get the info from the couch, instead of online.

Button has an icon, but still isn't transparent. When the button is clicked, it hides the description, but in it's absence the button becomes the height of the HBox. Must fix this.

Also need to give the info box a slightly-transparent background. Today (June 15) the image is very light, so white text doesn't display very well. Must fix this as well.

I'm also working on a rating system, so you can keep track of your favorite APoD pictures. Also, every picture is added to a slideshow, so you can browse previous pics as backgrounds.

Any input at this stage would be wonderful. I know this is a clumsy hack right now, but I'm working on improving that. Ideas are always welcome. I'm @nvsbl on Identica, and @nvsblmnstr on Twitter. Plus there's forum messages and all that jive, and the good old fashioned reply to this very thread. The choice is yours.

---

### Post by sisyphus1978 on 2010-06-21
I followed the first post. It has been working fine for a while, but recently it has stopped working unless I log in and log back out. Any ideas?

---

### Post by sisyphus1978 on 2010-06-22
Maybe it was something to do with the names of the actual pictures? Yesterday and today seem to have updated without a login-logout.

---

### Post by sisyphus1978 on 2010-06-29
I'm still not sure what's going on with this. Sometimes it updates, sometimes it doesn't. Perhaps the OP could weigh in?

---

### Post by o1911 on 2010-08-22
Apologies for my absence; I'm glad that my script has been some help, however.  I've since made many improvements to it, let me share that.  There's no more need for the cron hack either- just point gnome's background to the symbolic link created by the script, and it will update in real-time.

As for the additional information alongside the picture... that's an interesting idea.  I'm not sure how to get that to work, off the top of my head.  It appears nvsbl is onto something though.

```
#!/bin/bash
#Filename: apodwallpaper
#Purposes: Downloads NASA Astronomy Picture of the Day and displays it as the GNOME background 
#Author(s): acvwJosh of Ubuntu Forums, modified by Colin Dean <http://cad.cx>, o1911

# change this if you want the image to be in a different directory
DIRECTORY=$HOME/Pictures/APoD
cd $DIRECTORY

# fetch the apod site's text, to determine the latest apod
SITE=http://apod.nasa.gov/apod/index.html

if $(wget $SITE); then
	# the prefix of the filename is to be the current date
	FILENAME=$(cat $(echo $SITE | rev | cut -d "/" -f -1 | rev) | grep $(date +%Y) | head -1)

	# format this date to have underscores instead of spaces
	FILENAME=$(echo $FILENAME | tr " " "_")
	
	# check if today's file exists
	if [ ! -f $FILENAME* ]; then
		# if not, download image from apod site
		wget -A.jpg,.JPG -R.txt -r -l1 --no-parent -nH $SITE

		# find largest file (biggest res. picture)
		BIGFILESIZE=$(find apod/ -printf '%s\n' | sort -nr | head -1)
		
		# check if biggest file is a dir (no picture today)
		if [ $BIGFILESIZE == 4096 ]; then
		## there is no picture for today
			# set today's picture to be yesterday's
			YESTERDAY=$(( $(date +%s) - 86400 )) # 86400 seconds in a day
			ln -sf "$(find $DIRECTORY/ | grep -i $(date -d "@$YESTERDAY" +%Y_%B_%d))" "$HOME/wallpaper"
			
			## set today's picture to be a random one
			#NUMBEROFFILES=$(find . | wc -l)
			#NUMBER=$(( $RANDOM % $NUMBEROFFILES ))
			#ln -sf "$DIRECTORY/$(ls | tail -$NUMBEROFFILES | head -$NUMBER | tail -1)" $HOME/wallpaper
			
			rm -rf ap* *.apod robots.txt* index.html*
			exit 0
		fi
		
		## we have a picture for today
		# get its relative path for movement to ${DIRECTORY}
		BIGGESTFILE=$(find apod/ -size ${BIGFILESIZE}c)
		# also get its base filename to append
		BIGGESTFILENAME=$(find apod/ -size ${BIGFILESIZE}c -printf '%f\n')
		# declare our final filename for today's picture
		WALLPAPER=$FILENAME-$BIGGESTFILENAME
		# move it to the proposed directory
		mv $BIGGESTFILE $DIRECTORY/$WALLPAPER
	else
		WALLPAPER=$(find $DIRECTORY/ -name $FILENAME* -printf "%f\n")
	fi
else # wget failed. internet up?
	exit 1
fi

# as cron cannot set the wallpaper on its own, use a symbolic link to be a pointer to the background
rm $HOME/wallpaper
ln -sf "$DIRECTORY/$WALLPAPER" $HOME/wallpaper

# get rid of cruft
rm -rf ap* *.apod robots.txt* index.html*
exit 0

```

---

### Post by sierraindigo on 2011-01-29
> **o1911 said:**
> There's no more need for the cron hack either- just point gnome's background to the symbolic link created by the script, and it will update in real-time.

just looked this up again as my background had failed to update for a couple of days. when you say that the cron hack isn't needed anymore i take it you mean the .make_Xdbus steps? in which case i just call the script direct from cron now?

thanks for your work.

---

### Post by o1911 on 2011-01-29
> **sierraindigo said:**
> just looked this up again as my background had failed to update for a couple of days. when you say that the cron hack isn't needed anymore i take it you mean the .make_Xdbus steps? in which case i just call the script direct from cron now?

thanks for your work.

Yes that's right, just call apodwallpaper from cron and it will create a wallpaper symbolic link in your $HOME directory.  To use this as your background, just 'add' it like you normally would any other background ($HOME/wallpaper), but as cron updates the wallpaper day-to-day, the symbolic link gets updated, and thus your wallpaper changes automatically.

For what it's worth, I haven't noticed any problems in the last couple of days for me, but I may have made slight changes to the script without an update here; I'll update the newest post by me now.

Cheers!

---

### Post by sierraindigo on 2011-01-30
fantastic! thanks so much.

---

### Post by o1911 on 2011-03-07
Dumping my latest version here- now the script will use the latest apod file rather than just yesterday's; if there was no file for yesterday, nothing would happen.  I have also written the code to select a random apod if no apod exists for today, just 'comment out' the section of the code that uses 'yesterday's' apod and uncomment the random code just below.

Latest tinkering involved changing my naming convention for those files with 1 digit for the day of the month, now every file will have 2 digits for the day of the month (leading 0 if necessary).  If you want to change all of your saved pictures to this way, run this code:

```

<cd to your apod directory>
for x in *; do
    file=$(echo $x | cut -d"_" -f3- | cut -d- -f1)
    if [[ `echo ${#file}` == 1 ]]; then
        mv $x $(echo $x | sed 's/_\([0-9]\)-/_0\1-/')
    fi
done

```

My latest version of the script is here (I won't bother updating my latest posts in the hope that this saves confusion):

```
#!/bin/bash
#Filename: apodwallpaper
#Purposes: Downloads NASA Astronomy Picture of the Day and displays it as the GNOME background 
#Author(s): acvwJosh of Ubuntu Forums, modified by Colin Dean <http://cad.cx>, o1911

# change this if you want the image to be in a different directory
DIRECTORY=$HOME/Pictures/APoD
cd $DIRECTORY

# fetch the apod site's text, to determine the latest apod
SITE=http://apod.nasa.gov/apod/index.html

if $(wget $SITE); then
    # the prefix of the filename is to be the current date
    FILENAME=$(cat $(echo $SITE | rev | cut -d"/" -f-1 | rev) | grep $(date +%Y) | head -1)
    
    # if the day of the month is a single digit, put a 0 out the front
    FILENAME=$(echo $FILENAME | sed 's/ \([0-9]\)$/ 0\1/')
    
    # format this date to have underscores instead of spaces
    FILENAME=$(echo $FILENAME | tr " " "_")
    
    # check if today's file exists
    if [ ! -f ${FILENAME}* ]; then
	# if not, download image from apod site
	wget -A.jpg,.JPG -R.txt -r -l1 --no-parent -nH $SITE
	
	# find largest file (biggest res. picture)
	BIGFILE=$(find apod/ -printf '%s %f %p\n' | sort -nr | head -1)
	
	# check if biggest file is a dir (no picture today)
	if [ $(echo $BIGFILE | awk '{ print $3 }') == "apod/" ]; then
            ## there is no picture for today

	    # set today's picture to be the latest one instead
	    YESTERDAY=$(( $(date +%s) - 86400 )) # 86400 seconds in a day
	    PASTFILE=$(find $DIRECTORY/ | grep -i $(date -d "@$YESTERDAY" +%Y_%B_%d))
	    while [[ $PASTFILE == "" ]]; do
	    	YESTERDAY=$(( $YESTERDAY - 86400 ))
	    	PASTFILE=$(find $DIRECTORY/ | grep -i $(date -d "@$YESTERDAY" +%Y_%B_%d))
	    done
	    echo "No picture APoD for today. Using $PASTFILE instead."
	    rm $HOME/apod
	    ln -s $PASTFILE $HOME/apod

	    # # set today's picture to be a random one
	    # NUMBEROFFILES=$(find . | wc -l)
	    # NUMBER=$(( $RANDOM % $NUMBEROFFILES ))
	    # PASTFILE=$DIRECTORY/$(ls | tail -$NUMBEROFFILES | head -$NUMBER | tail -1)
	    # echo "No picture APoD for today. Using $PASTFILE instead."
	    # rm $HOME/apod
	    # ln -s "$DIRECTORY/$(ls | tail -$NUMBEROFFILES | head -$NUMBER | tail -1)" $HOME/apod

	    
	    rm -rf ap* *.apod robots.txt* index.html*
	    exit 0
	fi
	
	## we have a picture for today
	# structure the name by: date-base_filename
	WALLPAPER=$FILENAME-$(echo $BIGFILE | awk '{ print $2 }')
	# move the biggest file (relative path) to designated directory
	mv $(echo $BIGFILE | awk '{ print $3 }') $DIRECTORY/$WALLPAPER
    else
	WALLPAPER=$(find $DIRECTORY/ -name ${FILENAME}* -printf "%f\n")
    fi
else # wget failed. internet up?
    exit 1
fi

# as cron cannot set the wallpaper on its own, use a symbolic link to be a pointer to the background
rm $HOME/apod
ln -s $DIRECTORY/$WALLPAPER $HOME/apod

# get rid of cruft
rm -rf ap* *.apod robots.txt* index.html*
exit 0

```

---

### Post by sierraindigo on 2011-05-31
for some reason ubuntu is no longer setting the downloaded apod as my background. the apod is downloaded fine and the symbolic link in my home folder is for the new apod but my desktop doesn't update.

if i choose to change desktop background then the selected picture is the correct symbolic link file but the desktop doesn't update even after selecting a diff picture and then reselecting the apod link. when clicking through options for tiled, centred, zoom etc. the desktop changes between apods from the last couple of days while i have been trying to work out what is going on, even though there is no change in the apod link file.

any ideas? i have already checked permissions and can't see anything wrong. thanks

---

### Post by o1911 on 2011-06-01
> **sierraindigo said:**
> for some reason ubuntu is no longer setting the downloaded apod as my background. the apod is downloaded fine and the symbolic link in my home folder is for the new apod but my desktop doesn't update.

if i choose to change desktop background then the selected picture is the correct symbolic link file but the desktop doesn't update even after selecting a diff picture and then reselecting the apod link. when clicking through options for tiled, centred, zoom etc. the desktop changes between apods from the last couple of days while i have been trying to work out what is going on, even though there is no change in the apod link file.

any ideas? i have already checked permissions and can't see anything wrong. thanks

That is odd.  Are you using gnome2?  I've actually stopped using gnome/unity altogether in favour of KDE since gnome3 came out.  I happen to have a script that sets the input argument to your background, give it a try on your apod sym-link:

```

#!/bin/bash

# This script is intended to set the background of a GNOME session to the one specified.
# The first argument is the path of the picture file, and the second adjusts the picture aspect.
# If the second argument is not given, it will be assumed "scaled".
# Other valid arguments include "wallpaper" (tiled), "stretched", "centered" and "zoom".

if [[ $# != 2 ]]; then
    ASPECT="scaled"
else
    ASPECT=$2
fi

FILENAME=$(readlink -m $1)

gconftool-2 -t str --set /desktop/gnome/background/picture_filename "$FILENAME"
gconftool-2 -t str --set /desktop/gnome/background/picture_options "$ASPECT"

```

---

### Post by sierraindigo on 2011-06-05
> **o1911 said:**
> That is odd.  Are you using gnome2?  I've actually stopped using gnome/unity altogether in favour of KDE since gnome3 came out.  I happen to have a script that sets the input argument to your background, give it a try on your apod sym-link:


hmm. curiously running this works to update the background but only once: the background doesn't update to the the next day's apod even though the symlink has been changed unless i run the script on it again.

will try setting the input argument script to run in cron and see that works to get the background changing automatically.

i'm running unity on gnome2 btw, now i've got used to it i'm not finding it as awful as i did at first.

thanks again.

---

### Post by o1911 on 2011-06-05
> **sierraindigo said:**
> thanks again.

You're welcome.

Perhaps there has been a regression in nautilus (if that's still drawing the wallpaper when using unity); maybe killing it would cause the wallpaper to appear appropriately when nautilus restarts.  See how you go.

---

### Post by seanos on 2012-02-17
[This topic]("http://ubuntuforums.org/showpost.php?p=7210276&postcount=8") solved the "gconftool-2 not working from cron" problem for me.  Just add the lines for getting the dbus address to the setwallpaper script.

I also had some problems with the link being set for root when run from cron so I swapped $HOME for a MYHOME variable set to my home directory.

---

### Post by gmorph on 2012-03-16
A hack is to hijack the contest screen saver so it does the auto switching of the apod picture for you.

In 11.10 running Unity right click on your back ground and select "Change Desktop Background".  Select each one you see until its labelled Conquest (its picture may or may not have a little clock on it).  

Now, make a backup of the file 
/usr/share/backgrounds/contest/background-1.xml

Now edit that original file (need to sudo) and make it look like mine below:

<background>
  <starttime>
    <year>2009</year>
    <month>08</month>
    <day>04</day>
    <hour>00</hour>
    <minute>00</minute>
    <second>00</second>
  </starttime>
<!-- This animation will start at midnight. -->
  <static>
    <duration>1795.0</duration>
    <file>/home/**<your user name>**/apod.jpg</file>
  </static>
</background>

apod.jpg is the symbollic link to the apod picture.  Check your version of o1991's script to see what it is - it might just be apod.

The configuration above effective rotates to the same picture every 29minutes 55seconds which is the apod picture being updated by o1911's script.

Again, this is a hack but it gets the job done.

---

### Post by stblackbird on 2012-04-15
Hi guys. I am writing here because I wrote a simple script in python that sets the latest apod image as your desktop background on startup. I am using this for a few weeks now, and its working perfectly. Read the instructions in order to use (simple)
[http://sourceforge.net/projects/apodbackground/](http://sourceforge.net/projects/apodbackground/)

Any suggestions and help will be very welcome :D

---

### Post by SirKingChase on 2013-03-20
> **stblackbird said:**
> Hi guys. I am writing here because I wrote a simple script in python that sets the latest apod image as your desktop background on startup. I am using this for a few weeks now, and its working perfectly. Read the instructions in order to use (simple)
[http://sourceforge.net/projects/apodbackground/](http://sourceforge.net/projects/apodbackground/)

Any suggestions and help will be very welcome :D

Thanks for posting! "import commands" does not work with python3 so I have to execute it with python2, no big deal but I should point it out for the newbies finding this.

Also, if anyone is interseted in the geographic one posted in the first page,unless you are lucky enough to still be using gnome2, you need to change 2 lines to work with gnome3 all you need to do is change -


`gconftool-2 --type string --set /desktop/gnome/background/picture_filename "$photo"`; 
to

gsettings set org.gnome.desktop.background picture-uri "file:///yourfile"
and get rid of the following one that deals with zoom.

how to set gnome3 background -
[https://bbs.archlinux.org/viewtopic.php?pid=933248](https://bbs.archlinux.org/viewtopic.php?pid=933248)

import commands not working -
[https://bbs.archlinux.org/viewtopic.php?id=125971](https://bbs.archlinux.org/viewtopic.php?id=125971)

---

