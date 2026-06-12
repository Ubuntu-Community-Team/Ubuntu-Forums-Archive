---
title: "APOD? anyone"
date: 2007-05-31
forum: Desktop Environments
---

### Post by zombie-robot on 2007-05-31
the Astronomy Picture Of the Day was really cool in windows. Is there a way to port it to Ubuntu? or make a script to download it and apply it to the desktop automatically?

[http://antwrp.gsfc.nasa.gov/apod/astropix.html](http://antwrp.gsfc.nasa.gov/apod/astropix.html)

---

### Post by llamakc on 2007-05-31
Today's APOD has the larger jpg as the "href" so you could write a script to grab that line from the page source everyday, and then extract the path, pass that off to wget to grab the image, and place it wherever you want it on your filesystem. Of course I'm sure there's plenty of ways to do this, but that's one example.

I'm off to work but I'd be interested in cobbling something together like this.

---

### Post by llamakc on 2007-05-31
Found this on one of the Perl sites:

#!/usr/bin/perl

use strict;
use warnings;
use URI::URL;
use LWP::Simple qw/get/;

my $TOP = "http://antwrp.gsfc.nasa.gov/apod/";
my $IMGPATH = 'image/\d{4}/\w+.(gif|jpg|jpeg)';
my @timearray = gmtime();
my $time = sprintf "%04d%02d%02d", ($timearray[5]+1900), ($timearray[4]+1), ($timearray[3]);

my $content = get $TOP or die "Cannot get APOD Page\n";
my ($imgurl) = $content =~ m!($IMGPATH)!i;
$imgurl = url($imgurl,$TOP)->abs;

my $picture = get $imgurl or die "Cannot grab image: $!\n";

open(OUT, ">apod$time\.$2") or die "Cannot write to file: $!\n";
binmode(OUT);
print OUT $picture;
close OUT;

## END

That will drop the pics in whatever directory the script is ran from. I created an ~/apod directory and ran it like this:

cd ~/apod && ~/bin/jpeg-get.pl

I haven't looked up how to get it to scale or stretch to the desktop image via the commandline yet.

---

### Post by zombie-robot on 2007-05-31
I'll have to try this 

thankyou

---

### Post by llamakc on 2007-05-31
I've found several commandline scripts that can be pointed at a directory to change the wallpaper in Gnome. Are you using Gnome?

---

### Post by zombie-robot on 2007-05-31
yes and i found this:

#!/bin/sh

#Name: ranwp.sh
#Function: Wallpaper randomiser
#Adapted for Ubuntu Warty from suggestions
#found on [http://gnome-hacks.jodrell.net/](http://gnome-hacks.jodrell.net/)
#License: Public Domain

#Instructions: Place this script in a /bin directory
#and do a chmod +x <filename> on it.
#Then put it in a crontab or with your startup programs.
#Or both. Ubuntu Warty doesn't have a crontab editor,
#but you can install gcrontab via synaptic.

cd /usr/share/backgrounds
#Change this location if you keep your backgrounds elsewhere.
#Just one location allowed, sorry

IMGS=`find . -iname '*.jpg' -o -iname '*.png' -o -iname '*.svg'`
#You may want to get rid of the tiger head in
#/usr/share/backgrounds/scalable, in fact, blow
#that directory away!

N=`echo $IMGS | wc -w`
#Find out how many pictures we got

((N=RANDOM%N))
#Take a random number between 1 and N

BGNAME=`echo $IMGS | cut -d '/' -f $N | cut -d ' ' -f 1`
#We have to cut twice to get rid of an irritating " ." at the
#end after the first cut

# start of gconftool command - all on one line!
gconftool-2 -t str --set /desktop/gnome/background/picture_filename "/usr/share/backgrounds/$BGNAME"
# end of gconftool command

# start of gconftool command - all on one line!
gconftool-2 -t str --set /desktop/gnome/background/picture_options "stretched"
#Possible values are "none", "wallpaper" (eg tiled), "centered", "scaled", "stretched"
# end of gconftool command



Im going to try it now Ill have to tweak it. maybe you have something better?

---

### Post by llamakc on 2007-05-31
No, no that looks great. The gconf command at the end of the script is repeated twice for some reason. That must be an error, right?

---

### Post by zombie-robot on 2007-05-31
I dont know how to get it to work. When I run the desktop script I get a black desktop. I dont understand this part:

#Instructions: Place this script in a /bin directory
#and do a chmod +x <filename> on it.
#Then put it in a crontab or with your startup programs.
#Or both. Ubuntu Warty doesn't have a crontab editor,
#but you can install gcrontab via synaptic.


whats a /bin dir?
why do I have to do a chmod +x <filename> on it.
whats a crontab?

sorry im a semi noob

---

### Post by zombie-robot on 2007-05-31
sweet I got it!!

Im stoked thanks llamakc. 

so now i guess its time to try to combine the two scripts.

---

### Post by llamakc on 2007-05-31
Look up an Ubuntu howto page for crontab. Run the script to grab the image at one time, and then the other script to apply the wallpaper about five minutes after.

---

### Post by zombie-robot on 2007-05-31
I will figure out a script to do this:

Run the script to grab the image at one time, and then the other script to apply the wallpaper about five minutes after.

---

### Post by Joe Momma on 2007-11-14
Has anyone worked on this in a while?

I would like to put the script in my localrc file and have it run once a day, grabbing the picture of the day, and setting it to my background.  However I don't know how to do this.

Everyday it should overwrite the previous day's image, and I would like it to stretch it to my screen size too.

---

### Post by Joe Momma on 2007-11-15
I did it, if anyone is interested.  The following is the previous script, slightly modified to apply the wallpaper.  I saved it as ~/APOD/apod.sh.  Then I did a crontab -e and added the line " 00 08 * * * ~/APOD/apod.sh " to run it everyday at 8 am.



#!/usr/bin/perl

use strict;
use warnings;
use URI::URL;
use LWP::Simple qw/get/;

my $TOP = "http://antwrp.gsfc.nasa.gov/apod/";
my $IMGPATH = 'image/\d{4}/\w+.(gif|jpg|jpeg)';
my @timearray = gmtime();
my $time = sprintf "%04d%02d%02d", ($timearray[5]+1900), ($timearray[4]+1), ($timearray[3]);

my $content = get $TOP or die "Cannot get APOD Page\n";
my ($imgurl) = $content =~ m!($IMGPATH)!i;
$imgurl = url($imgurl,$TOP)->abs;

my $picture = get $imgurl or die "Cannot grab image: $!\n";

## The following line saves all images
#open(OUT, ">apod$time\.$2") or die "Cannot write to file: $!\n";
## The following line overwrites images everyday
open(OUT, ">apod\.$2") or die "Cannot write to file: $!\n";

binmode(OUT);
print OUT $picture;
close OUT;

my $DIR = `pwd`;
chomp $DIR;
my $COMMAND =   "gconftool-2 -t str --set /desktop/gnome/background/picture_filename";
$COMMAND = $COMMAND . ' "' . $DIR . "/apod\.$2" . '"';
print "$COMMAND \n";
qx/ $COMMAND /;

$COMMAND =   'gconftool-2 -t str --set /desktop/gnome/background/picture_options "stretched"';
print "$COMMAND \n";
qx/ $COMMAND /;

## END

---

### Post by llnk on 2007-11-22
thanks for this. I used to have an apod app in XP. I made the switch to Ubuntu yesterday, now it's feeling a lot more like home. :)

---

### Post by acvwJosh on 2008-01-26
Hello!  Sorry to dig up an old thread, but I just made this today, and thought others might be interested.  I wanted to have the APOD update and set it to be my wallpaper every morning, so I made this bash script to do it.  It's my first bash script, so I'm welcome to criticism / suggestions.  It's in a folder within my home folder called .wallpaper, and it's set to call the script from a cron file.  

It's not perfect, but it looks like it'll do the job okay.  I'm open to suggestions for improvement!

```
#!/bin/bash

# download image from apod site
wget -A.jpg -R.txt -r -l1 --no-parent -nH http://antwrp.gsfc.nasa.gov/apod/astropix.html

# move image from obscure folder to main folder, rename image
find ./apod -name "*.jpg" | while read line ; do
	mv "$line" "wallpaper.jpg"
done

# set image to wallpaper
gconftool-2 -t string -s /desktop/gnome/background/picture_filename "blank.jpg"
gconftool-2 -t string -s /desktop/gnome/background/picture_filename "/home/josh/.wallpaper/wallpaper.jpg"
gconftool-2 -t string -s /desktop/gnome/background/picture_options "zoom"

```

---

### Post by cdean on 2008-03-26
Fantastic, gentlemen and ladies. acvwJosh, I extended your script and added some instructions for people and made it a little more multi-user friendly.

Perhaps we could extend this even more and make it some kind of thing that pokes up a tray information dialog whenever the picture is updated, and the dialog contains the text for the APOD.

```
#!/bin/bash
#Filename: apodwallpaper
#Location: ${HOME}/.bin
#Purposes: Downloads NASA Astronomy Picture of the Day and displays it as the GNOME background 
#Author(s): acvwJosh of Ubuntu Forums, modified by Colin Dean <http://cad.cx>

#add the following line to your crontab if you want to run this hourly
#10   *  *   *   *     apodwallpaper

#add this line if you want to run it every four hours
#10 0,4,8,12,16,20 * * * apodwallpaper

#add this line if you want to run it every twelve hours
#10 0,12 * * * apodwallpaper

#add this line if you want to run it daily 
#10 0 * * * apodwallpaper

#don't forget to put this script in your $PATH.
#I usually add ${HOME}/.bin to my path in .bash_profile and put my scripts there

#change this if you want the image to be in a different directory
FILENAME=apodwallpaper
APODWALLPAPER=${HOME}/.${FILENAME}

mkdir -p ${APODWALLPAPER} && cd ${APODWALLPAPER}

# download image from apod site
wget -A.jpg -R.txt -r -l1 --no-parent -nH http://antwrp.gsfc.nasa.gov/apod/astropix.html

# move image from obscure folder to main folder, rename image
find ./apod -name "*.jpg" | while read line ; do
mv "$line" "${FILENAME}.jpg"
done

# set image to wallpaper
gconftool-2 -t string -s /desktop/gnome/background/picture_filename "blank.jpg"
gconftool-2 -t string -s /desktop/gnome/background/picture_filename "${APODWALLPAPER}/${FILENAME}.jpg"
gconftool-2 -t string -s /desktop/gnome/background/picture_options "zoom"

#get rid of cruft
rm -rf apod robots.txt
```

---

