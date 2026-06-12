---
title: "Wallpaper Changing Applet has gone hogwild!"
date: 2009-06-24
forum: Desktop Environments
---

### Post by greensimian on 2009-06-24
Hello,

I am using Unbuntu 9.04 and I am trying to customize it withe fresh pimp style. In my ceaseless pursuit for pimp juice I enabled the Wallpaper Applet that comes with Toolbar.  I decided that I didn't want the applet to change my wallpaper so I changed the timer to 0.  I thought it was there to begin with.

Now my computer is changing Wallpaper so fast that I can't maintain Windows Focus long enough to click on something.  I turned off my computer to let it boot, after a lengthy desk check I now get the following message when trying to open the Wallpaper Tray Applet

*[COLOR=Red]"The panel encountered a problem while loading "OAFIID:wp_tray" Do you want to delete the applet from your configuration?[/COLOR]*

And my options are *[COLOR=Red]Don't Delete and Delete[/COLOR]*.  Neither seems to do anything noticitble.

Has anyone seen this?  Any idea how to fix this?

---

### Post by sDaddy on 2009-08-18
Did the same thing, same results..  tried removing the package and reinstalling it..    also tried another fix from [http://ubuntuforums.org/showthread.php?t=1178083&highlight=wallpaper-tray](http://ubuntuforums.org/showthread.php?t=1178083&highlight=wallpaper-tray)  and still the same error.   

Just started on Ubuntu today and am at a total loss

---

### Post by sDaddy on 2009-08-18
Looks like I have it solved from my end...

removed wallpaper-tray using "sudo apt-get remove wallpaper-tray"  it will tell you that there are librarys that can be removed and tells you how (see next step)

next, removed the librarys that go with it using "sudo apt-get autoremove"

then went in to the file system and deleted the wp_tray directory  (home/username/.gconf/apps/) (hidden area so you have to enable view hidden files)

Verified the app was no longer on the system, rebooted, reinstalled wallpaper-tray, rebooted and now the app works perfectly.

Misconfigured it again on purpose and ended up with the same errors, and followed the same steps to get it working again.

Give it a try!

---

### Post by dalesd on 2009-12-06
Thanks, sDaddy.  I had the same error and your procedure fixed it.

---

### Post by sDaddy on 2009-12-06
After playing with this now for several months, I found that when the directory I use for wallpapers isn't present  (changed name of directory or disconnect the drive they are on etc...), this is what happens.  Of course, setting the options wrong causes it also..

---

### Post by everdred on 2010-04-20
> **sDaddy said:**
> After playing with this now for several months, I found that when the directory I use for wallpapers isn't present  (changed name of directory or disconnect the drive they are on etc...), this is what happens.  Of course, setting the options wrong causes it also..

Thanks for this, sDaddy! This was just what I needed.

---

