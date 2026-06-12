---
title: "Desktop wallpaper slide show builder?"
date: 2010-06-05
forum: Desktop Environments
---

### Post by wkulecz on 2010-06-05
Any tools to assemble a set of images into a Gnome desktop wallpaper slide show -- like the Cosmos one in the default selection?

I can see its a folder with the images and an xml file that controls the "playback".  Presumably there is a reasonably easy tool to use to create my own short of reverse engineering the xml files.

--wally.

---

### Post by sites on 2010-06-05
Try the 'pictures folder' screensaver.  Put your images in a folder and point this screensaver to it in Preferences->Screensaver

---

### Post by sites on 2010-06-05
Wait that was all wrong.

Install xscreensaver

*sudo apt-get install xscreensaver xscreensaver-data-extra*

*killall gnome-screensaver*

Start up the xscreensaver settings gui, choose GLSlideshow, then click the Advanced tab.  There you'll see a section labeled "Image manipulation".  Make sure "choose random images" is the only box checked in this section and type the directory of your image folder into the box below it.  I had trouble using the browse button, but typing the directory in worked fine. Test your GLSlideshow.  Last step is to uninstall xscreensaver, but not the extras.

*killall xscreensaver*

*sudo apt-get remove xscreensaver*

Reboot, open gnome-screensaver gui, choose GLSlideshow and everything should work.

---

### Post by wkulecz on 2010-06-05
The question is not about running a screensaver.  I want to create another desktop background like the Cosmos one that is there by default.

Even better would be if there was some way to assign a different background to each of the virtual desktops.

---

### Post by n213978745 on 2010-06-05
> **wkulecz said:**
> The question is not about running a screensaver.  I want to create another desktop background like the Cosmos one that is there by default.

Even better would be if there was some way to assign a different background to each of the virtual desktops.


If you are searching for a software that can assign different background for each workspace, this software may help you and the official site is:

[http://wallpapoz.akbarhome.com/index.html](http://wallpapoz.akbarhome.com/index.html)


But sadly the software doesn't include in Ubuntu Software Center.  So you may need to figure it out by ourselves on how to install it and make it work.  I used this software before on different Linux system and it worked fine.

EXCEPT that you may have a trouble to remove it!  I tried to remove it before, and somehow my workspaces' wallpaper is still changing even I uninstalled it already.  So you have to click "stop daemon" before you uninstalled it.

And also the developer has stopped develop this software for a long time.

---

### Post by wkulecz on 2010-06-05
Thanks, I can live without seperate wallpaper/backgrounds for the multiple destops, as I'm not too keen on unmaintained things that aren't essential, but I'd still like to know how to make my own autocycling wallpaper like the Cosmos one.

---

### Post by sites on 2010-06-09
Ah, now i see my mistake.  This is like the Pictures desktop background on Macs where you can set it to change every few seconds/minutes/daily.. correct?  I don't know how to do that.

---

### Post by angry_johnnie on 2010-06-09
[This]("http://ubuntuforums.org/showthread.php?p=5751005")

courtesy of guywithcable and I :popcorn:

Just edit the script a little bit (it's about 2 years old), so that it doesn't fade in/out.  Nautilus will do that by itself, i think.

Source is found in the tar.gz file.

---

