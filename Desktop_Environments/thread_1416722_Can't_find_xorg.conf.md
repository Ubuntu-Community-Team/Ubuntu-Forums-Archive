---
title: "Can't find xorg.conf"
date: 2010-02-26
forum: Desktop Environments
---

### Post by tnsmart on 2010-02-26
I am trying to edit the xorg.conf file as described here:

[https://wiki.ubuntu.com/X/Config/Resolution#Setting%20resolution%20changes%20in%20xorg.conf%20--%20resolution%20lower%20than%20expected](https://wiki.ubuntu.com/X/Config/Resolution#Setting%20resolution%20changes%20in%20xorg.conf%20--%20resolution%20lower%20than%20expected)

However, I cannot find the xorg.conf file anywhere.  Any ideas?

Thanks.

---

### Post by gixpaulie on 2010-02-26
Hi,

This may be a long shot but do a search though nautilus for it, if not go to another console screen via Ctrl-Alt-F2/F6 and try reinstall xorg

---

### Post by n0dix on 2010-02-26
You have to generate the file. Then you can find it in /etc/X11/ directory.

---

### Post by tnsmart on 2010-02-26
The only thing a search of xorg.conf returned was xorg.conf.5.g.

How can I generate the file?  I tried following this: [http://www.freebsd.org/doc/handbook/x-config.html](http://www.freebsd.org/doc/handbook/x-config.html)  under 5.4.2 but any of the commands I run, I get: "Fatal server error: Server is already active for display 0…"

The help is appreciated.

---

### Post by tnsmart on 2010-02-26
If it helps,  I'm trying to get a dual monitor setup to work right.  I've got one monitor plugged into the DVI port on my computer and the other into VGA port.  When I originally start up my computer, my DVI display is fine, in the Display Preferences, I get the option for 1280x1024.  But the VGA only gives me options for 640x480 and 800x600.

However, after playing around with settings enough I get the VGA to give me 5 different resolutions, but not the 1280x1024 that I need.  After restarting my computer again, this all resets back to the too small options.

I have tried reinstalling xorg, but it did not help.

---

### Post by n0dix on 2010-02-26
> **tnsmart said:**
> The only thing a search of xorg.conf returned was xorg.conf.5.g.

How can I generate the file?  I tried following this: [http://www.freebsd.org/doc/handbook/x-config.html](http://www.freebsd.org/doc/handbook/x-config.html)  under 5.4.2 but any of the commands I run, I get: "Fatal server error: Server is already active for display 0…"

The help is appreciated.

Ati, Nvidia or Intel? Do you installed the video driver?

---

### Post by tnsmart on 2010-02-26
I believe it's intel.  The ports are right on the motherboard.  I have not installed any drivers.  Hardware Drivers under the Administration Preferences say that "No proprietary drivers are in use on this system."  Looking at the Synaptic Package Manger, xserver-xorg-video-i740 and xserver-xorg-video-intel are already installed.

Can you tell me how I can generate the xorg.conf file?

---

### Post by n0dix on 2010-02-26
The true is, you don't need a xorg.conf file. When you install the open driver for Intel card you don't need a xorg file. 

To create the file do:
$ sudo Xorg -configure

---

### Post by darolu on 2010-02-26
Ubuntu 9.10 does not generates a xorg.conf file by default, it is not needed (hasn't been needed for a while) but you can still use it; you can to create it yourself, open a terminal and go to /etc/X11/ and create it with your favourite text editor (nano is installed by default):
```
$ cd /etc/X11/
$ sudo nano xorg.conf
```
You save with ctrl+o and exit with ctrl+x (in nano).
If you are not a command line fan, you can do it with gedit, press ALT+F2 and type:
```
gksu gedit /etc/X11/xorg.conf
```
Here is a example of a xorg.conf file: [http://dev.gentoo.org/~fmccor/docs/xorg/xorg.conf/xorg.conf.html](http://dev.gentoo.org/~fmccor/docs/xorg/xorg.conf/xorg.conf.html)

---

### Post by tnsmart on 2010-02-26
I don't see any other way to get the 1280x1024 resolution I need, and for it to stay.  When I type Xorg -configure, I get the same thing as when I tried following this: [http://www.freebsd.org/doc/handbook/x-config.html](http://www.freebsd.org/doc/handbook/x-config.html) under 5.4.2. 

Any of the commands I run, I get: "Fatal server error: Server is already active for display 0…"

---

### Post by darolu on 2010-02-26
First you need to determine what monitor is dsplay 0 and what is display 1; anyways this link may help you: [http://maketecheasier.com/how-to-setup-dual-monitors-with-xrandr/2009/06/01](http://maketecheasier.com/how-to-setup-dual-monitors-with-xrandr/2009/06/01)

You can add the 1280x1024 mode with xrandr as well, more documentation here:
[http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)

---

### Post by tnsmart on 2010-03-04
So I finally got it to work by editing xorg.conf to look like:

> Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor    "Configured Monitor"
    Device    "Configured Video Device"
  SubSection "Display"
    Depth 24
    Modes "1280x1024" "1280x1024"
    Virtual 2560 1024
    EndSubSection
  EndSubSection
EndSectionRunning 'xrandr' in Terminal now returns this:
> Screen 0: minimum 320 x 200, current 2560 x 1024, maximum 8192 x 8192
VGA1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 286mm
   1280x1024      65.7*+   75.0  
   1024x768       75.1     70.1     60.0  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     60.0  
   720x400        70.1  
DVI1 connected 1280x1024+1280+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0 +   75.0* 
   1024x768       75.1     70.1     60.0  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     60.0  
   720x400        70.1  
The problem is that whenever I restart or start up the computer, I get a message stating:
"Ubuntu is running in low-graphics mode

The following error was encountered. You may need to update your configuration to solve this.

(EE) Problem parsing the config file
(EE) Errot parsing the config file"

I have to tell it to "Run Ubuntu in low-graphics mode for just one session"

Once I do this, it starts up and sometimes it displays fine and sometimes it doesn't.  Anyway I can prevent this and have it restart normally?

---

### Post by tnsmart on 2010-03-05
So the first time I edited the xorg.conf file as I mentioned above, it worked except for that error.  After that, it hasn't worked since.  I would still appreciate any help.

---

### Post by bomgd3 on 2010-06-09
I have the same exact problem!  This seems like one of those ridiculously obvious things that no one in the community seems to notice because everyone is more advanced...

I installed the Radeon drivers and now my CPU usage is extremely high.  I saw in numerous guides that I should take a look at Xorg.conf.  However, I can't generate it because I have the same error--Server is already active.  Maybe we can't do Xorg -configure while Xorg is running?  In this case, how do we kill Xorg and go to a bare terminal?

---

### Post by unkilbeeg on 2010-06-09
In a terminal, type
```
sudo /etc/init.d/gdm stop
```

Since they're not using "real" SysV init, that's not the "approved" method any more, but it should work.  It's what I always use.

---

### Post by Moonking on 2010-06-10
Hi,I'm new here, been a Suse and Redhat guy since 1998 and now I'm trying Kubunta 10.04
I have the same problem of not being able to set my default res, keeps reverting back, I sudo xrandr -s 1024x768 (the res I want) and see it did set it as default
 
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1600 x 1200
default connected 1024x768+0+0 0mm x 0mm
   1600x1200      65.0     60.0  
   1400x1050      75.0     70.0     60.0  
   1280x1024      75.0     60.0  
   1280x960       85.0     60.0  
   1360x768       60.0  
   1152x864       75.0     85.0     70.0     60.0  
   1024x768       85.0*    75.0     70.0     60.0     87.0  
   800x600        85.0     75.0     72.0     60.0     56.0     65.0  
   640x480        85.0     75.0     73.0     67.0     60.0  
   640x400        85.0  
   512x384        85.0     75.0     70.0     60.0     87.0  
   400x300        85.0     75.0     72.0     60.0     56.0  
   320x240        85.0     75.0     73.0     60.0  
   320x200        85.0  

now if I understand correctly, this is not called on startup thus throwing me back to  1600x1200 
So I ask what is being called upon at startup ?
somewhere I think remember where I could get xrandr to startup at some run level but was wondering why not "sudo kate" and edit the beast itself ?
P.S I have no xorg.config file (at least not yet LOL!)

---

### Post by Moonking on 2010-06-11
anyway on to bigger and better problems
phonon can't play a wave , since I'm a musician and have a home studio it sucks that I can't play a wave :( tested amarok and Kaffine, but audcity and ardour work thank god
any Hope?
:guitar:

---

### Post by Moonking on 2010-06-24
Got Amarok playing waves and mp3's by changing to GStreamer backend
but Equalizer not supported 

first 
"sudo aptitude install phonon-backend-gstreamer"
then 
"sudo apt-get install libxine1-ffmpeg gstreamer0.10-plugins-ugly"
then switched the backend
see more here
[http://amarok.kde.org/wiki/Download:Kubuntu](http://amarok.kde.org/wiki/Download:Kubuntu)

---

