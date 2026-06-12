---
title: "Multiple Starting File Manager - Loads of them at Start up."
date: 2011-08-15
forum: Desktop Environments
---

### Post by darren123web on 2011-08-15
Hey Guys,

I have a problem with 'Starting File Manager' completeley filling my taskbar on startup.

There could be 100 of them for all I know, as the taskbar ends up dividing into tiny slices for each.

How do I find out what is causing this?  Is there a log file I can check or some way to repair ubuntu off the Live CD?

Recently installed some updates.  Last night tried reinstalling Nautilus and Gnome (did that with commands from Ctrl Alt F1 ) but that has not helped.

Any help gratefully received!


I'm running Ubuntu 10.04 LTS (64bit)
Dell Inspiron 530

I'm no Ubuntu / Linux expert, but I can try to find any info / logs required

Thanks
Darren

---

### Post by darren123web on 2011-08-20
Well, a reinstall it is then!

Gonna try it with separate partition this time for /home folder, and see how it goes...

D

---

### Post by wimmelis on 2011-10-17
Dear all, 


Experiencing exactly the same problem here. Anyone with any ideas ? A particular update maybe ?
I used to be able to log out and then next time I logged on, it was normal again ... only worked twice :(



Regards, 

WM

---

### Post by drs305 on 2011-10-17
I used to have that problem very often on a new installation. Fortunately no longer.

But this is what I had to do to stop the auto-spawning of nautilus back in Lucid/Maverick:
Make a backup of the file and then manually change the following line using a text editor as root.

```
sudo cp /usr/share/applications/nautilus.desktop /usr/share/applications/nautilus.desktop.bak
gksu gedit /usr/share/applications/nautilus.desktop
 
```

> 
[COLOR="Red"]X-GNOME-AutoRestart=true[/COLOR]
*to*
X-GNOME-AutoRestart=false

---

### Post by UncleBoarder on 2012-11-22
I've read everything I could find on this, including the bug reports. I tried everything, including drs305. There appears to be no solution that works yet.  But my problem occurred when I upgraded my system.  So I reverted to an older version of my video driver and the problem was SOLVED!  :):):)

If you're using an AMD driver you might want to downgrade.  My problem version was amd-driver-installer-12-1-x86.x86_64.run.

The version that works is ati-driver-installer-11-12-x86.x86_64.run

You can find old drivers on [http://support.amd.com](http://support.amd.com)

Good luck.
--------------
If it works great, don't upgrade!

---

### Post by UncleBoarder on 2012-11-22
Uh... It DID work, I know it did.  But after I reinstalled (I'd tried so much stuff to get this working I wanted to be ce  rtain)... anyway after a reinstall with the older video driver it failed again. :-(   So, 4 more hours of searching/reading I think I found the answer.  [https://bugs.launchpad.net/nautilus-elementary/+bug/664793](https://bugs.launchpad.net/nautilus-elementary/+bug/664793)        

Which says, disable RGBA in your File Management Preferences.    Open Nautilus (any folder window). In nautilus window choose edit->preferences, in tweak tab, disable rgba. reboot.      

This worked for me and I guess that means I need to reinstall once more to be certain.    Here we go...

---

### Post by UncleBoarder on 2012-11-23
IT WORKS!  Even with the new video driver!     

So the only problem is a bug in the RGBA code.  Disable RGBA and your golden!!!

---

### Post by wildmanne39 on 2012-11-23
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

