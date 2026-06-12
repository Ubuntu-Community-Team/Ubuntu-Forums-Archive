---
title: "NWN or Ubuntu"
date: 2005-09-18
forum: Gaming &amp; Leisure
---

### Post by rseymour on 2005-09-18
I'll try to keep this short.

I'm trying to switch over to Ubuntu at home.  I don't play a lot of games, but I do like nwn.  I did get it working last week after a lot of pain.  Like always, after I'd gotten it running and playable, I got overconfident and tried to set up the movies ... it was a smart move as I hosed the game so bad that I figured the best/easiest way to recover it was to reinstall Ubuntu and then the game. (This is the one place or at least one of the places I don't remember if I've duplicated from my earlier install to may latest ... my earlier install was from a daily breezy install cd, but I don't remember the date; the latest is from the breezy preview)

My system seems to be up and running (foxconn microatx board running an AMD Athlon 64 4000+ chip; 2 gigs of ram; 600 gigs of storage on SATA drives, and a BFG nvidia 6600GT.

I used synaptic to get the nvidia driver (7667) and the nvidia-settings program; then i used the config sudo nvidia-glx-config enable to enable the driver.  I've manually commented out the Load="GLcore" and Load="dri" lines from the module section of xorg.conf.  At boot, I do get the nvidia splash screen and glxgears works.  

As I said, this is the same setup that was working before?  But this time around, I'm having no luck.

When I had nwn running before, I'd used the platinum cd install method.    I've also tried the bioware download process (resources, client, and update), the DVD install method, and the Ravage installer.  With cd/dvd installs, running ./fixinstall doesn't find the nwm directory until after I've applied the patch.  When I run ./nwn, I get "./nwmain: error while loading shared libraries: libXxf86vm.so.1: cannot open shared object file: No such file or directory" regardless of the install method.

I've done a google search for libXxf86vm.  It looks like the closest error to mine is "fixed" at [http://www.blitzbasic.com/Community/posts.php?topic=43363](http://www.blitzbasic.com/Community/posts.php?topic=43363).  Doesn't seem like this will work though, because I don't have libXxf86vm.a.

Does it look like I've missed something the second time around?  I'm wondering if the problem might be related to the updates/upgrades that are coming fast and furious as they try to get breezy finaled?

Would appreciate any help.

---

### Post by Cthulhu on 2005-09-18
try
```
apt-get install libxxf86vm1
```

---

### Post by Perfect Storm on 2005-09-18
If everything fails, try these installers: [http://icculus.org/~ravage/nwn/](http://icculus.org/~ravage/nwn/)

---

### Post by rseymour on 2005-09-18
Thanks for the responses.

I checked the lib and it looked like I had the latest ... apt-get install confirmed this.  I'd  tried the Ravage installer and it didn't work for me either.

playing around with it a little more, it looks like I've got a file/path problem.  running ldd nwmain, it was missing 4 files.  running the export line out of the nwh script file (export LD_LIBRARY_PATH=./lib:./miles:$LD_LIBRARY_PATH) and then running ldd nwmain again, it found 2 of the files, 1 located in /lib and the other located in /miles.  I finally copied the other 2 files, libXxf86vm.so.1.0.0 and libdrm.so.1.0.0 to /miles and created symbolic links to the files (libXxf86vm.so.1 and libdrm.so.1).  The symbolic file names are the files needed, but after export it still not finding them.

Any suggestions?

---

### Post by rseymour on 2005-09-23
OK ...

Never had any luck with my original libXxf86vm.so.1 error.  I tried loading the 32-bit version of Ubuntu and had some limited success with the base nwn package, but it was sporadic.  Then I tried out Mandriva 2006 and OpenSuse.  Had different issues with both distros, but since I didn't like either as much as I like Ubuntu, I reinstalled Ubuntu last night.  Thinking that the problem might be fixed by updates, I tried loading nwn again.  Still no luck.

After updating this a.m., I tried again.  No more libXxf86vm error ... now it was libGL.so.1.  After trying to export LD_LIBRARY_PATH, I tried ldd nwmain and found that the only file not found was the libGL path.  After tracing the file down, I found the link broken. Relinked it and ran ldconfig.

Using the platinum install from CD, nwn now seems to be running.  (somewhere in the process, I got the extract tar's to work to the point of getting sound w/o picture).  Will keep my fingers crossed.

---

### Post by Kemotaha on 2005-09-27
Somewhere in the back of my head, when I installed it I thought I had to install a couple of libraries inside one of the NWN directories.  I don't remember which one though and I am not at home to check.  I won't be able to check for a little while because I am house sitting my parent's house but if you send me a PM, I can check in a few days.

---

### Post by madjo on 2005-09-27
I recently installed my NWN Platinum DVD edition following these instructions:
[http://nwn.bioware.com/forums/viewtopic.html?topic=417536&forum=72](http://nwn.bioware.com/forums/viewtopic.html?topic=417536&forum=72)
and it worked almost flawlessly (a small resolution problem aside, which was easily fixed by trying out a few resolutions (and restarting X after nwn crashed with one or two resolutions) ;) )

---

