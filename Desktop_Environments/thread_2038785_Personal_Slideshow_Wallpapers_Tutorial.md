---
title: "Personal Slideshow Wallpapers Tutorial"
date: 2012-08-07
forum: Desktop Environments
---

### Post by gareththered on 2012-08-07
If my memory serves me well (and to be honest, it lets me down on quite a few occasions these days!), you could add slideshow wallpapers to earlier versions of Ubuntu, but currently System Settings -> Background allows you to add images but not slideshows.

There are a few tutorials/threads around that explain how to add slideshows to the system so that all users can access them, but I couldn't find any that adds slideshows to the users' home directory.  I'm using Gnome-Shell on my machine, but I'm certain the principles are the same for Unity too.

First of all, you need to create the directory hierarchy that will hold your XML files:
```
mkdir -p ~/.local/share/gnome-background-properties
```Next, create the file that will inform the system that you have a new wallpaper:
```
gedit ~/.local/share/gnome-background-properties/MyFirstSlideshowCollection.xml
```You can actually call the file anything as long as it ends in '.xml' as all files in the directory will be read.
This file contains a <filename> tag that points to another XML file that describes your slideshow.  Mine is as follows:-
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE wallpapers SYSTEM "gnome-wp-list.dtd">
<wallpapers>
  <wallpaper>
    <name>My 1st Slideshow</name>
    <filename>.local/share/backgrounds/wallpaper1/My1stSlideshow.xml</filename>
    <options>zoom</options>
    <pcolor>#2c001e</pcolor>
    <scolor>#2c001e</scolor>
    <shade_type>solid</shade_type>
  </wallpaper>
</wallpapers>
```The XML file that describes my new slideshow is therefore:
```
.local/share/backgrounds/wallpaper1/My1stSlideshow.xml
``` but it could be located anywhere and named anything as longs as the <filename> tag above points to it. Note the following though:

[LIST]
[*]The <name> tag is the 'pretty' name displayed in System Settings
[*]The <options>, <pcolor>, <scolor> and <shade_type> tags are optional.  If they are not supplied, System Settings->Background will give you the option to select them.
[/LIST]
 Before you save this file, ensure the 'gedit' option to save backups has been disabled.  If you don't, you will find backup files (ending in ~) in the directory and System Settings will display your wallpaper twice!  Not the end of the world, but annoying all the same.

Next, edit this slideshow XML file to configure the actual images used:
```
mkdir -p ~/.local/share/backgrounds/wallpaper1
gedit ~/.local/share/backgrounds/wallpaper1/My1stSlideshow.xml
```This file will contain the filename, paths and timings for the slideshow.  Mine looks like this:
```
<background>
  <starttime>
    <year>2012</year>
    <month>01</month>
    <day>01</day>
    <hour>00</hour>
    <minute>00</minute>
    <second>00</second>
  </starttime>
  <static>
    <duration>300.0</duration>
    <file>.local/share/backgrounds/wallpaper1/Beautiful-Nature.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>.local/share/backgrounds/wallpaper1/Beautiful-Nature.jpg</from>
    <to>.local/share/backgrounds/wallpaper1/Ubuntu.jpg</to>
  </transition>
  <static>
    <duration>300.0</duration>
    <file>.local/share/backgrounds/wallpaper1/Ubuntu.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>.local/share/backgrounds/wallpaper1/Ubuntu.jpg</from>
    <to>.local/share/backgrounds/wallpaper1/Beautiful-Nature.jpg</to>
  </transition>
</background>
```Save the file.  Most of this is quite self-explanatory, but just in-case: 
[LIST]
[*]The file paths and filenames will need to be adjusted to suit your wallpaper images.  Mine happen to be stored in the same place as the XML file, but it doesn't have to be.
[*]The start time will need to be in the past for you to see the slideshow working.
[*]Duration is in seconds.
[*]The above displays a static image for 5 min (300 sec) and then takes 5 seconds to transition to the next image.
[*]You can have as many files as you want - I made this two so that it isn't too long.
[/LIST]
 To make life easier, there are tools and scripts available that will create this XML file for you.  Google is your friend here!

If all goes well, you should be able to see the new slideshow in System Settings -> Background.

Some people have reported that their systems crash if these files are incorrectly configured or point to non-existent files.  I didn't find this to be the case, but that doesn't mean you shouldn't be careful!  Save all important work beforehand.

I hope this helps someone.

---

### Post by xfctr on 2012-08-09
I suggest you try Variety Wallpaper Changer - it is a new application that I've been working on during the past 2-3 months and I think it is shaping as one of the best wallpaper changers for Linux. Response from users so far has been vastly positive.

With it you can build a big collection of great wallpapers in no time and change very easily between them, manually or automatically in a slideshow-like manner.

[Video demo]("http://www.youtube.com/watch?v=7bmpNR7mQ4k")
[Screenshots]("http://imgur.com/a/BFMJn")
[Project page and source-code]("https://launchpad.net/variety")

Installation (installs in /opt):
```

sudo add-apt-repository ppa:peterlevi/ppa
sudo apt-get update 
sudo apt-get install variety
```
Or simply grab the latest deb from [here]("https://launchpad.net/~peterlevi/+archive/ppa/+packages")

It should fairly soon appear in Ubuntu Software Center as well, I'm waiting for the review process to finish.

---

### Post by cortman on 2012-08-09
Nice write up! This would make a great wiki page.
xfctr, as soon as your app gets approved, a footnote for that would be great.
OP, would you like to make a new wiki page on this? I'll help if you want. :)

---

### Post by stinkeye on 2012-08-09
> **xfctr said:**
> I suggest you try Variety Wallpaper Changer - it is a new application that I've been working on during the past 2-3 months and I think it is shaping as one of the best wallpaper changers for Linux. Response from users so far has been vastly positive.

With it you can build a big collection of great wallpapers in no time and change very easily between them, manually or automatically in a slideshow-like manner.

[Video demo]("http://www.youtube.com/watch?v=7bmpNR7mQ4k")
[Screenshots]("http://imgur.com/a/BFMJn")
[Project page and source-code]("https://launchpad.net/variety")

Installation (installs in /opt):
```

sudo add-apt-repository ppa:peterlevi/ppa
sudo apt-get update 
sudo apt-get install variety
```
Or simply grab the latest deb from [here]("https://launchpad.net/~peterlevi/+archive/ppa/+packages")

It should fairly soon appear in Ubuntu Software Center as well, I'm waiting for the review process to finish.

Just  having a look at *variety* and it looks to be very well thought out. Well done.
I like the auto download and filter section.
The favourites is also a good idea.

---

### Post by gareththered on 2012-08-09
xfctr - Variety is excellent!  In fact, it's the first desktop changer that I found that works well.  Brilliant.

However, my tiny tutorial was purely to explain how to configure Gnome's built in wallpaper changer.  This doesn't need any extra software running in the background - just some images and some XML!  Mind you, that does mean that it's rather limited in comparison to Variety.  I suppose it's a case of user choice. I'm leaving Variety running on my system at the moment just to see what new images it downloads :-)

cortman - is it worthy of a Wiki?  It would need expanding if it were to be considered for one.  I'm more than willing if the interest is there though.

---

### Post by cortman on 2012-08-09
> **gareththered said:**
> xfctr - Variety is excellent!  In fact, it's the first desktop changer that I found that works well.  Brilliant.

However, my tiny tutorial was purely to explain how to configure Gnome's built in wallpaper changer.  This doesn't need any extra software running in the background - just some images and some XML!  Mind you, that does mean that it's rather limited in comparison to Variety.  I suppose it's a case of user choice. I'm leaving Variety running on my system at the moment just to see what new images it downloads :-)

cortman - is it worthy of a Wiki?  It would need expanding if it were to be considered for one.  I'm more than willing if the interest is there though.

I think your tutorial is great- the only other wallpaper/slideshow tutorial on the wiki I could find was about using another program for it, not pure Gnome like yours.
I think it'd make terrific wiki material as-is- change wording in a few places, etc.
PM me if you want a hand converting it. :)

---

### Post by xfctr on 2012-08-13
**UPDATE: **Variety Wallpaper Changer is now in Ubuntu Software Center, albeit a really old version - it will take some time till they update it to a decently recent one. Just run Software Center and search for "variety", or click [here: apt://variety]("apt://variety"). I kindly ask everyone who likes the program to write a review there - it is still competing in the Ubuntu App Showdown contest and users' votes in the Software Center will count for the final results. Thank you.

---

