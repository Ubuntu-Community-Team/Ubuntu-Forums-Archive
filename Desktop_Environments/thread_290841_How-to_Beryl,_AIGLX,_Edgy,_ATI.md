---
title: "How-to: Beryl, AIGLX, Edgy, ATI"
date: 2006-11-01
forum: Desktop Environments
---

### Post by igknighted on 2006-11-01
Ok, off of a fresh install of Edgy this is what I did to get Beryl working flawlessly on my ATI x800GTO card.  This *should* work with any ATI card up to the x850 (r480 chip) with relatively minor tweaking (if any at all).  Here goes:

I installed with the alternate CD, so on my first boot I booted into recovery mode.  I typed:

```
nano /etc/X11/xorg.conf
```

I then found the section "Device".  The driver listed (by default) is ati.  Change this to radeon.  Write the rest of your section like this (although don't touch Identifier or BusID section).  You may need to comment out the AGPMode and the FastWrite lines, some cards will not support this.

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X850 Pro (R480)"
	Driver		"radeon"
	Option		"AGPFastWrite" "yes"
	Option		"AGPMode" "4"
	Option		"ColorTiling" "on"
	Option		"EnablePageFlip" "true"
	Option		"AccelMethod" "EXA"
	Option		"XAANoOffScreenPixMaps"
	Option		"RenderAccel" "true"
	Option		"DRI" "true"
	BusID		"PCI:1:0:0"
```

Save this file (ctrl+o, ctrl+x) and reboot.  Log into gnome as normal, take care of any updates, then add this line to your /etc/apt/sources.list

```
deb http://www.beerorkid.com/compiz edgy main-edgy
```

also run this code in a terminal window:

```
wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
```

and

```
sudo apt-get update
```

Next, install Beryl by running

```
sudo apt-get install beryl-core beryl-plugins beryl-plugins-data emerald beryl-settings beryl-manager beryl beryl-dev emerald-themes
```

After this you should be done!  Type Beryl-Manager in a terminal window and Beryl should start.

Note:  There is a bug in Beryl that may cause a flickering, a workaround for this is to go to System -> Administration -> System Moniter and click on the processes tab.  From the list, choose the Beryl-Manager and kill the process.  All of your effects will still be there, but adjust your settings as you need then kill the manager because thats where the issue seems to be.

---

### Post by hawk88 on 2006-11-01
the repository doesn't work :???: 

**output:**
Unable to find expected entry  main/binary-i386/Packages in Meta-index file (malformed Release file?)

---

### Post by igknighted on 2006-11-01
oops, typo... should end with main-edgy not main, I will fix it above

---

### Post by pony-tail on 2006-11-02
Did you get this to work without the "fglrx" drivers ?
My 9800xt (agp) and X850XT-PE (PCI-E) cards do not appear to work at all with the "radeon" drivers The X850 will not even display 2D with "ati" or "radeon " or for that matter "vesa" with "vga" I get a display but it is unuseable .
Is everything working at proper speed ?

---

### Post by Hobo Joe on 2006-11-02
I have a question, is it ok to put 'radeon' into the config file if you have fglrx drivers?

Will everything still work properly?

(sorry about noob question, I just got Ubuntu a couple days ago.)

---

### Post by darrenm on 2006-11-02
Yes it is. X will just load Radeon instead of fglrx

I have a 9600XT and the only way I can get the radeon driver to work is with the following config in xorg.conf  ```
  Section "Device"
    Identifier      "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        Option "DRI" "true"
        Option "ColorTiling" "on"
        Option "EnablePageFlip" "true"
        Option "AccelMethod" "XAA"
        Option "XAANoOffscreenPixmaps"
        Option "GARTSize" "64"
#       Option "RenderAccel" "true"
#       Option "AGPMode" "2"
#       Option "AGPFastWrite" "on"
        EndSection

```

---

### Post by Hobo Joe on 2006-11-02
Thanks a bunch. I'll test this and see if it works.

---

### Post by igknighted on 2006-11-02
> **pony-tail said:**
> Did you get this to work without the "fglrx" drivers ?
My 9800xt (agp) and X850XT-PE (PCI-E) cards do not appear to work at all with the "radeon" drivers The X850 will not even display 2D with "ati" or "radeon " or for that matter "vesa" with "vga" I get a display but it is unuseable .
Is everything working at proper speed ?

My x800GTO identifies as an x850 because it doesn't use the x800 chip, it uses the r480 chip that the x850 uses.  However, the page [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) does mention that some PCI-E cards have issues with the radeon driver.  It does say that the 9800xt works fine, so try commenting out some of the lines they suggest to see if you can find a setup that works.

---

### Post by Hobo Joe on 2006-11-02
I don't have a PCI-E card, and I use the fglrx drivers. I have X1300 AGP version.

When I edited the xorg.conf and said radeon drivers, Ubuntu froze on the bootup screen...

Help would be appriciated.

---

### Post by Hobo Joe on 2006-11-02
Ok, I think I found the problem, I don't have direct rendering enabled, but I found [this]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") link, I'm gonna try it as soon as I get home from school.

Will I still want to have it set as 'radeon' rather than 'fgrlx' if I follow this tut?

Thanks.

---

### Post by igknighted on 2006-11-02
According to this page [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver), the radeon driver only supports 3d rendering on cards up to the x800 family.  I don't believe it works with the x1300 yet.  This could have changed with edgy, however, so it could be worth a shot.

---

### Post by drdaz on 2006-11-02
Hi there,

Using those directions I get quite close to a functional beryl but sadly not quite. My desktop background switches to an enlarged version of the console used to spawn beryl-manager. It changes occasionally, mostly when moving windows. Here's a screenshot:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=18755&stc=1&d=1162500448[/IMG]

Any suggestions as to how to fix this would be most appreciated.

EDIT: I'm on a Dell Inspiron 6000 w/ Mobility x300 (32MB onboard RAM).

/drdaz

---

### Post by CarpKing on 2006-11-02
> **Hobo Joe said:**
> Ok, I think I found the problem, I don't have direct rendering enabled, but I found [this]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") link, I'm gonna try it as soon as I get home from school.

Will I still want to have it set as 'radeon' rather than 'fgrlx' if I follow this tut?

Thanks.

The fglrx drivers lack support for AIGLX, and you must uninstall them in order to get DRI with the radeon drivers.  If you must use fglrx, you'll have to look into XGL instead of AIGLX.  It works, but it screws up some other stuff that uses 3d if you run it at the same time.

---

### Post by mahy on 2006-11-03
Alrite, i've got ATI Mobility Radeon X300 PCI Express card, how should i modify xorg.conf to get AIGLX working? And how do i install 'radeon' driver? Or is it already installed? (right now i'm using fglrx driver) TIA

---

### Post by darrenm on 2006-11-03
Just follow the howto in the first post.

---

### Post by igknighted on 2006-11-03
> **mahy said:**
> Alrite, i've got ATI Mobility Radeon X300 PCI Express card, how should i modify xorg.conf to get AIGLX working? And how do i install 'radeon' driver? Or is it already installed? (right now i'm using fglrx driver) TIA

I did this off of a fresh install, but you will need to remove the fglrx drivers for this to work I believe.  Not sure if apt can do this or if theres more to it than that.

---

### Post by darrenm on 2006-11-03
I didnt. My fglrx drivers are still installed. When X loads it just loads the radeon module rather than the fglrx module. Cant see anywhere else it could conflict?

---

### Post by CarpKing on 2006-11-03
> **darrenm said:**
> I didnt. My fglrx drivers are still installed. When X loads it just loads the radeon module rather than the fglrx module. Cant see anywhere else it could conflict?

Do you have DRI working?  I had read that fglrx screws up some of the linking necessary for the radeon driver to do direct rendering.

---

### Post by mahy on 2006-11-04
Thank you all guys,

in the end  i used  Xgl, coz i didn't wanna mess with xorg.conf and fglrx drivers. You know what was the problem? I had to kill xfwm4 before starting beryl, that's all. Now i've got 3D desktop working.

---

### Post by Julius on 2006-11-04
I have a laptop with a PCI-e Ati mobility radeon x300 too. I installed edgy the other day and haven't installed any important thing, or touched any configuration.

Apparently I'm using the "ati" driver in XORG. Should I install any driver different than that one, or I can just simply follow the how to?

---

### Post by CarpKing on 2006-11-04
> **Julius said:**
> I have a laptop with a PCI-e Ati mobility radeon x300 too. I installed edgy the other day and haven't installed any important thing, or touched any configuration.

Apparently I'm using the "ati" driver in XORG. Should I install any driver different than that one, or I can just simply follow the how to?

Should be fine.  The "ati" driver should detect that you have a Radeon card and use the "radeon" driver automatically.

---

### Post by darrenm on 2006-11-05
> **CarpKing said:**
> Do you have DRI working?  I had read that fglrx screws up some of the linking necessary for the radeon driver to do direct rendering.

```
darrenm@darrenm-desktop:~$ xdriinfo 
Screen 0: r300

```
I assume that means DRI is working?

---

### Post by Julius on 2006-11-05
OK, I followed the how to and it works!
And after tweaking it a little, I LOVE IT! But firefox is now somewhat slower. Scrolling is noticeably slower  when beryl is on.

---

### Post by agentstewie on 2006-11-12
> **igknighted said:**
> Ok, off of a fresh install of Edgy this is what I did to get Beryl working flawlessly on my ATI x800GTO card.  This *should* work with any ATI card up to the x850 (r480 chip) with relatively minor tweaking (if any at all).  Here goes:

I installed with the alternate CD, so on my first boot I booted into recovery mode.  I typed:

```
nano /etc/X11/xorg.conf
```

I then found the section "Device".  The driver listed (by default) is ati.  Change this to radeon.  Write the rest of your section like this (although don't touch Identifier or BusID section).  You may need to comment out the AGPMode and the FastWrite lines, some cards will not support this.

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X850 Pro (R480)"
	Driver		"radeon"
	Option		"AGPFastWrite" "yes"
	Option		"AGPMode" "4"
	Option		"ColorTiling" "on"
	Option		"EnablePageFlip" "true"
	Option		"AccelMethod" "EXA"
	Option		"XAANoOffScreenPixMaps"
	Option		"RenderAccel" "true"
	Option		"DRI" "true"
	BusID		"PCI:1:0:0"
```

Save this file (ctrl+o, ctrl+x) and reboot.  Log into gnome as normal, take care of any updates, then add this line to your /etc/apt/sources.list

```
deb http://www.beerorkid.com/compiz edgy main-edgy
```

also run this code in a terminal window:

```
wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
```

and

```
sudo apt-get update
```

Next, install Beryl by running

```
sudo apt-get install beryl-core beryl-plugins beryl-plugins-data emerald beryl-settings beryl-manager beryl beryl-dev emerald-themes
```

After this you should be done!  Type Beryl-Manager in a terminal window and Beryl should start.

Note:  There is a bug in Beryl that may cause a flickering, a workaround for this is to go to System -> Administration -> System Moniter and click on the processes tab.  From the list, choose the Beryl-Manager and kill the process.  All of your effects will still be there, but adjust your settings as you need then kill the manager because thats where the issue seems to be.
hmm you think that if i buy a radeon x1600 aiglx will work?

---

### Post by Treviño on 2006-11-12
To use this way, don't forget to remove the fglrx kernel module (if you don't want remove the other fglrx related packages...)

```
sudo apt-get remove fglrx-kernel-$(uname -r)
sudo /etc/init.d/{k,g}dm stop
sudo rmmod fglrx
sudo modprobe radeon
sudo /etc/init.d/{k,g}dm force-reload

```

Those are the settings I use to make Aiglx working in my Mobility Radeon 9700:
> Section "Device"
        Identifier      "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
        Driver          "radeon"
        Option "AccelMethod" "XAA" # Use XFree86 Acceleration Architecture
#      Option "AccelMethod" "EXA" # Too slow here...
        Option "XAANoOffscreenPixmaps" "true"
        Option "AccelDFS"    "0" # Better "0" using AGP
        Option "AGPMode" "4" # AGP Speed
        Option "AGPSize" "128" # AGP Aperture Size
#      Option "AGPFastWrite" "1" # Here it crashes X... Try if it works for you
        Option "GARTSize" "64"
        Option "RingSize" "8"
        Option "BufferSize" "2"
        Option "EnablePageFlip" "true"
        Option "ColorTiling" "true"
        Option "EnableDepthMoves" "true"
#      Option "MergedFB" "true"
        Option "MergedXinerama" "true"
#      Option "UseFBDev" "true"
        Option "RenderAccel" "true" # Enable the hardware render acceleration
        Option "mtrr" "on"
        Option "DisplayPriority" "HIGH"
#      Option "SubPixelOrder" "none"
        Option "DPMS"
        Option "DynamicClocks" "on"
        Option "MonitorLayout" "LVDS, AUTO"

        BusID "PCI:1:0:0" #mine...

Regarding beryl... The only way to make it working is running
beryl-xgl --replace&
:o

---

### Post by tribaal on 2006-11-14
Method works great, thanks.

Does anyone know if it's possible to get a more up-to date radeon driver? I.E is it possible to download and compile a bleeding edge open source radeon driver without getting all of xorg?

- trib'

---

### Post by Treviño on 2006-11-14
Here you are: [xserver-xorg-video-ati_6.6.3-0-3v1ubuntu0_i386.deb]("http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/xserver-xorg-video-ati_6.6.3-0-3v1ubuntu0_i386.deb")

Btw you can take individual packages from [http://ftp.x.org/pub/individual/driver/](http://ftp.x.org/pub/individual/driver/)

Cvs infos are in the package description.

However there aren't so great changes, maybe upgrading the dri module whould be better, but I've tried to use a newer version and simply it stops my AIGLX working (or better, KDE freezes while loading a composite manager also if the xorg log seems ok...)

Please, report any thought about the 6.6.3 version of the ati radeon driver...

Thanks!

---

### Post by fuoco on 2006-11-14
What about ppc ? ;)

---

### Post by Treviño on 2006-11-14
I don't have that arch... Simply package it by your self...
You can also use the debian testing base for packaging...

---

### Post by StreetSmart on 2006-11-14
I got this error when doing the apt-get update

W: GPG error: [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
W: You may want to run apt-get update to correct these problems


Any ideas?

---

### Post by Treviño on 2006-11-14
Simple...
```
gpg --keyserver subkeys.pgp.net --recv 31A5F97FED8A569E
gpg --export --armor 31A5F97FED8A569E | sudo apt-key add -
```

---

### Post by Circus-Killer on 2006-11-16
excellent howto. worked perfectly for me except one thing.

   Option     "TripleBuffer" "yes"

i added the above option to the device section which seemed to help with a bit of lag i was getting on the animation. with adding the triplebuffer option, the lag is now gone.

also, can you please ask a mod to sticky this thread, as i think it is a perfect howto for people using the open source drivers.

EDIT: after thinking about it, i did hash out those two lines which you said might need hashing. so i think that for those who hash out those 2 lines should add the triplebuffer line. i could be wrong, but its what worked for me.

---

### Post by hit0442 on 2006-11-18
I can't make it work in my Radeon Xpress 200M. After I command beryl-manager, it goes to a white screnn and than ack to gdm.

---

### Post by Treviño on 2006-11-19
Xpress 200m isn't supported due to its &#8220;strange&#8221; (shared) memory configuration... Anyway its support is planned.

Btw, [Circus-Killer]("http://ubuntuforums.org/member.php?u=114557") I didn't understand well... :P Do you suggest or not to add that value?
I thought it was just for Nvidia cards.... :o

---

### Post by Circus-Killer on 2006-11-19
okay, lemme try break it down.

in the very first post of this thread, the poster suggested that some people may need to hash out the following lines:

        Option		"AGPFastWrite" "yes"
	Option		"AGPMode" "4"

now, i am one of those people. however, even though after hashing those lines out i got everything working, it still seemed to lag. this is when i added the triple buffer option.

so basically, to sum it up, if you hashed out those couple of lines and everything works but laggy, try adding the triple buffer option, it might help.

---

### Post by Cl1mh4224rd on 2006-11-19
OK. This doesn't seem to be working. With a fresh install, switching the driver from "ati" to "radeon" (plus the options) actually results in *worse* performance. Dragging windows too fast gets very chunky, I have 100% CPU usage for a couple minutes before it calms down, and minimizing a window leaves the borders of windows underneath as an after-image of the window I just minimized for a full second.

I have and X800GTO (R400).

Additionally, I can't even import the GPG key. I copy/paste the command given and get this:

```
$ wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
Password:--16:53:55--  http://www.beerorkid.com/compiz/quinn.key.asc
           => `-'
Resolving www.beerorkid.com... 208.113.152.130
Connecting to www.beerorkid.com|208.113.152.130|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,692 (1.7K) [text/plain]

100%[====================================>] 1,692         --.--K/s             

16:53:55 (17.89 KB/s) - `-' saved [1692/1692]



```
...and just sits there. I don't get the "OK" that I would expect and I'm not sent back to the command prompt. If I hit Ctrl+C I get:

```
sudo: pam_authenticate: Conversation error
```
I seriously doubt the GPG issue has anything to do with the changes I had made, though. I had installed the available distro updates immediately after installing the OS, and right before modifying xorg.conf and rebooting. When I logged back in, I no longer had any sound.

Weeee...

EDIT: GPG is fine. It just decided to work the fifth time I tried it. :rolleyes:

---

### Post by igknighted on 2006-11-19
What options did you add into xorg.conf?  Some of them may not work with your setup.  Also, is your card AGP or PCI-E?  The radeon drivers have issues with some PCI-E cards (including the x850, which the x800GTO is for all intents and purposes)

---

### Post by RobNyc on 2006-11-20
Damn I can't wait till it works on the x1600 =\

---

### Post by Treviño on 2006-11-20
Anyway..... > (WW) RADEON(0): Option "TripleBuffer" is not used

---

### Post by Super King on 2006-11-20
Edit: Nevermind, it works when I pasted in what Trevino said.

---

### Post by Cl1mh4224rd on 2006-11-20
> **igknighted said:**
> What options did you add into xorg.conf?  Some of them may not work with your setup.  Also, is your card AGP or PCI-E?  The radeon drivers have issues with some PCI-E cards (including the x850, which the x800GTO is for all intents and purposes)
I've used the the options in your OP, and even tried Circus-Clown's suggestion (commenting out the "AGP*" options and adding the "TripleBuffer" option).

The card is AGP.

(Correction to my previous post. The chipset on my card is actually R430 according to Ubuntu.)

Another symptom: scrolling in Firefox is *extremely* slow...

Edit: When starting "beryl-manager", does this mean anything significant?

```
$ beryl-manager
$ libGL warning: 3D driver claims to not support visual 0x4b
```

---

### Post by Treviño on 2006-11-21
No, that's absoluteky a known thing.. Don't worry ;)

---

### Post by b1g4L on 2006-11-21
WOW! That's all I can say. I got Beryl/XGL to work on my ATI 9800 pro. Thanks for the tutorial....this is more awesome than I could have possibly imagined.

Which option can I change to keep the menu from animating....I can't seem to find that. Thanks again!

---

### Post by Treviño on 2006-11-22
Using a 9800? :o
I knew that the radeon driver didn't work with it...

---

### Post by Nakkis on 2006-11-24
Thanks for the tutorial, I got my Beryl working with AIXGL using Radeon 7000. 
It's bit slow (but so is the card).

---

### Post by adds2one on 2006-11-26
Hello,

I have got Beryl working with XGL on my ATI Mobility Radeon R250 9000 M9 card using the official ATI fglrx driver but I am not happy with XGL.

So I want to get Beryl working using AIGLX with the Ubuntu Radeon driver but I am having trouble getting the Radeon driver to work properly (no DRI).

I have tried replacing "fglrx" with "ati" or "radeon" in /etc/X11/xorg.conf but when I check with "glxinfo | grep render" I find that I have no direct rendering. 

I am confused because everything I read says that the radeon driver should work (have DRI) with Beryl.

Do I need to actually remove the fglrx driver? If so how would I do this? I  installed it following the instructions here: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

I would be so greatful if anyone could help me to get the radeon driver to have DRI so that I could run Beryl with AIGLX!:) 

Thanks

---

### Post by adds2one on 2006-11-26
I finally got fglrx removed and am now using the radeon driver which is giving me direct rendering.

I am still having some small problems. When I type glxinfo | grep render
I get this output:
```

libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes
OpenGL renderer string: Mesa DRI R200 20060602 AGP 1x TCL
```

and when I run beryl-manager from a terminal I get this:

```
libGL warning: 3D driver claims to not support visual 0x4b

```

The problem I am experiencing in Beryl is that the window borders do not appear around apps. 

Here is my xorg.conf

```
Section "Device"
        Identifier  "ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"

Driver "radeon"
Option "DRI" "true"
Option "ColorTiling" "on"
Option "EnablePageFlip" "true"
## Some may experience very poor performance without hashing the following line.
Option "AccelMethod" "EXA"
Option "XAANoOffscreenPixmaps"
Option "RenderAccel" "true"
#Option "AGPMode" "x" <- x may be 2 or 4 depending on your system
Option "AGPFastWrite" "on"
BusID       "PCI:1:0:0"

EndSection

```

When I closed Firefox I noticed this error in the terminal:

```
(beryl-manager:5703): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed
```


I am running Edgy.

I have done some searching but found no solution to the no window border thing yet. Any thoughts?

---

### Post by Treviño on 2006-11-27
> libGL warning: 3D driver claims to not support visual 0x4b
[B]THIS ISN'T A BUG... 
[/B]
Set your AGPMode as your agp speed (check for it in your chipset vendor) in your xorg.conf, then imho XAA AccelMethod is better with beryl (with r300 is quicker, especially on rotating cube or when there are many windows opened)

Bye

---

### Post by CarpKing on 2006-11-27
> **adds2one said:**
> The problem I am experiencing in Beryl is that the window borders do not appear around apps. 

I've had this happen sometimes too.  Try right-clicking on the Beryl Manager icon in the tray and selecting "Reload Window Manager."  If the minimize, close, etc buttons don't show up, also select "Reload Window Decorator."  I hope this works for you.

---

### Post by Cl1mh4224rd on 2006-11-27
> **Cl1mh4224rd said:**
> I've used the the options in your OP, and even tried Circus-Clown's suggestion (commenting out the "AGP*" options and adding the "TripleBuffer" option).

The card is AGP.

(Correction to my previous post. The chipset on my card is actually R430 according to Ubuntu.)

Another symptom: scrolling in Firefox is *extremely* slow...
Anyone?

I'm still getting absurdly poor performance...

---

### Post by cvmostert on 2006-11-28
Hi and thanks for the howto,

i did as you said, but beryl hangs, and sometimes the gdm restarts... 

i will seek for other problems.. 

thanx anyway

---

### Post by Pathfinder_ on 2006-11-28
Hi, i installed beryl using a guide from beryl wiki. i did not amke any changes to to my xorg.conf and beryl ran fine. however after i stumbled upon this guide, i noticed that you add stuff to xorg.conf. after searching some more i found out that by adding "TripleBuffer" "true" to my xorg.conf beryl would speed up and it did. Now, i'm wondering if i should all that different  stuff like 
```
Option "DRI" "true"
Option "ColorTiling" "on"
Option "EnablePageFlip" "true"
## Some may experience very poor performance without hashing the following line.
Option "AccelMethod" "EXA"
Option "XAANoOffscreenPixmaps"
Option "RenderAccel" "true"
#Option "AGPMode" "x" <- x may be 2 or 4 depending on your system
Option "AGPFastWrite" "on"
```
to my xorg.conf.
here's how it looks now:
```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon RV250 If [Radeon 9000 Pro]"
	Driver		"ati"
	Option          "TripleBuffer" "true"
	BusID		"PCI:1:0:0"
EndSection
```

---

### Post by Get_Ya_Wicked_On on 2006-11-29
> **Cl1mh4224rd said:**
> Anyone?

I'm still getting absurdly poor performance...


[http://bugs.beryl-project.org/trac/ticket/1](http://bugs.beryl-project.org/trac/ticket/1)

There was another one on there that was much more "documented."

But Beryl's servers got pretty ******, as far as I know.

Point being it's a bug.

---

### Post by igknighted on 2006-11-29
> **Pathfinder_ said:**
> Hi, i installed beryl using a guide from beryl wiki. i did not amke any changes to to my xorg.conf and beryl ran fine. however after i stumbled upon this guide, i noticed that you add stuff to xorg.conf. after searching some more i found out that by adding "TripleBuffer" "true" to my xorg.conf beryl would speed up and it did. Now, i'm wondering if i should all that different  stuff like 
```
Option "DRI" "true"
Option "ColorTiling" "on"
Option "EnablePageFlip" "true"
## Some may experience very poor performance without hashing the following line.
Option "AccelMethod" "EXA"
Option "XAANoOffscreenPixmaps"
Option "RenderAccel" "true"
#Option "AGPMode" "x" <- x may be 2 or 4 depending on your system
Option "AGPFastWrite" "on"
```
to my xorg.conf.
here's how it looks now:
```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon RV250 If [Radeon 9000 Pro]"
	Driver		"ati"
	Option          "TripleBuffer" "true"
	BusID		"PCI:1:0:0"
EndSection
```

It cant hurt to try it out... as always, back up before you change anything, but go ahead and try adding more potions and perhaps your performance will improve... and if anything messes up, just go back to your backup.

---

### Post by Cl1mh4224rd on 2006-12-02
> **Get_Ya_Wicked_On said:**
> [http://bugs.beryl-project.org/trac/ticket/1](http://bugs.beryl-project.org/trac/ticket/1)

There was another one on there that was much more "documented."

But Beryl's servers got pretty ******, as far as I know.

Point being it's a bug.
Well... damn. Thanks.

---

### Post by praxis22 on 2006-12-02
Well, it was a real **** to get it all working, but it does (finally) work.

I'm Running:
Radeon X800XT (AGP)
AMD64 3800+
1Gb RAM
ASRock 939A8X-M Mobo
Edgy 6.10 64Bit

My BIOS has AGP x8, 64Mb Aperture, AGP Fast Write enabled.

I first tried to use the ATI fglrx drivers, no joy, after much mucking about I just did a straight re-install from scratch.

The second time around I tried to use the "radeon" driver in xorg.conf, X wouldn't even load, so I reverted. Then I followed the instructions on this page:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Which worked!

My xorg.conf now looks like this:

Section "Device"
        Identifier      "ATI Technologies, Inc. R420 JK [Radeon X800]"
        Driver          "ati"
        Option          "AGPMode"       "8"
        Option          "AGPSize"       "64"
#       Option          "AGPFastWrite"  "on"
        Option          "AccelMethod"   "XAA"
        Option          "ColorTiling"   "on"
        Option          "DynamicClocks" "on"
        Option          "RenderAccel"   "true"
        Option          "TripleBuffer"  "true"
        Option          "DRI"           "true"
        Option          "EnablePageFlip"        "true"
        Option          "EnableDepthMoves"      "true"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
EndSection

Even though my BIOS has AGP Fast Write, enabled, if I have it set in xorg.conf, X will not load and/or reload. YMMV

This is what I get out of glxinfo:

glxinfo
name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x4b
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20060815 AGP 8x TCL
OpenGL version string: 1.3 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_fragment_program, GL_ARB_imaging, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_MESAX_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_gpu_program_parameters, 
    GL_EXT_histogram, GL_EXT_packed_pixels, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x4b 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

This is what I get out of xdriinfo:

xdriinfo
Screen 0: r300

If yours doesn't look something like this (direct rendering enabled with DRI working) it's probably not going to work.

I then then installed Beryl as described here:

[http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy)

To load the PGP key you have to run this command:

wget [http://beryl-mirror.lupine.me.uk/1609B551.gpg](http://beryl-mirror.lupine.me.uk/1609B551.gpg) -O- | sudo apt-key add -

Failing that you download the key, (right click, "save as") and then manually add it to the: System -> Administration -> Software Sources tool under the "Authentication" tab, hit the "Import Key File" button and add the key that way.

Then you need to add the beryl repository. Even though I'm running amd64 I could see no way to explicitly add a 64 bit tree, so I just used the default:

deb [http://compiz-mirror.lupine.me.uk/](http://compiz-mirror.lupine.me.uk/) edgy main

Updated:

sudo apt-get update

Then I installed beryl:

sudo apt-get install beryl-core beryl-plugins beryl-plugins-data emerald beryl-settings beryl-manager beryl emerald-themes

From the shell I ran:

beryl --display :0 &
emerald --replace &

At which point it said:

XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
libGL warning: 3D driver claims to not support visual 0x4b
Initiating splash
beryl: water: GL_ARB_fragment_program is missing
Reloading all options.

Up came the splash screen and beryl lurched into view, I say "lurched" as it lags a fair bit. Also the frame around Firefox is missing and it's suddenly a lot slower, especially at scrolling. This seems to be a common problem from what I can tell.

That said, it's all fairly slick and silly, dragging windows around is far more fun that it ought to be :)

Because of this I think I'm going to save it as a separate session, there are instruction on how to do this here:

[http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/AiGLX#Configuring_Beryl](http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/AiGLX#Configuring_Beryl)

But I've not done this yet, so it may or may not work, caveat emptor, and all that.

So, keep plugging away at it, you'll get there in the end. Now I'm off to bed as it's gone 3am here, I shall play and tweak some more tomorrow. I'll update if I find anything useful.

---

### Post by numbers1thru9 on 2006-12-03
I have installed a fresh clean copy of edgy and have my radeon 9600 mobility running the fglrx drivers and have the composite set to 0 to enable direct rendering. I want to use aiglx and I followed the guide and it beryl wont load, because it gives a no composite extension error. If i take that section out of the xorg.conf file then fglrx has the default Mesa direct rendering and then beryl wont even load. I really want this to work, does anyone know how to get it to work?

---

### Post by igknighted on 2006-12-03
This guide is for ATI cards that are NOT using the fglrx driver.  fglrx does not support AIGLX at all.  If you want to use AIGLX give the open source driver a shot.

---

### Post by Treviño on 2006-12-04
I' building the *xserver-xorg-video-ati* driver pratically on each [git]("http://gitweb.freedesktop.org/?p=xorg/driver/xf86-video-ati.git") update...
If anyone want it, I could add a un *unstable* version to my repo...

With the latest version (20061203) I get good glxgears values:
> 8090 frames in 5.0 seconds = 1617.977 FPS
8296 frames in 5.0 seconds = 1659.060 FPS
8199 frames in 5.0 seconds = 1639.759 FPS
8501 frames in 5.0 seconds = 1700.121 FPS
8495 frames in 5.0 seconds = 1697.184 FPS
8569 frames in 5.0 seconds = 1713.726 FPS
Use this command to get the same
```
glxgears -printfps & sleep 31 && killall glxgears
```

---

### Post by fuoco on 2006-12-04
> **Treviño said:**
> I' building the *xserver-xorg-video-ati* driver pratically on each [git]("http://gitweb.freedesktop.org/?p=xorg/driver/xf86-video-ati.git") update...
If anyone want it, I could add a un *unstable* version to my repo...

With the latest version (20061203) I get good glxgears values:

Use this command to get the same
```
glxgears -printfps & sleep 31 && killall glxgears
```

I don't assume you can make a ppc deb, right? 
Also, I think the mesa packages are also important for 3d in radeon drivers.

---

### Post by Treviño on 2006-12-04
Well... No... I can't (I've only an i386...)!
Anyway if anyone want I can attach my "debian" files to make packages for other arch...

Regarding Mesa, I've tried to compile the newer mesa drivers, but with them it hangs when loading AiGLX or other 3d apps :(
BTW I've new libdrm packages (and also kernel modules version 2.3)... They seem to gave a quite good improvement (modules first of all)...

---

### Post by marios88 on 2006-12-07
I got it up and running with my X800 SE PCI-E ,it is just awesome and only 15mb of ram!!!!

I have too noticed a delay while browsing with firefox and more cpu usage when i load pages...


But i do get an error an lock-up when i try glxgears

When i start beryl i get this error

```

libGL warning: 3D driver claims to not support visual 0x4c
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
libGL warning: 3D driver claims to not support visual 0x4c

```

Is there something i can do???


Also i cannot get the water effects working

```
beryl: water: GL_ARB_fragment_program is missing
```

---

### Post by igknighted on 2006-12-07
> **marios88 said:**
> I got it up and running with my X800 SE PCI-E ,it is just awesome and only 15mb of ram!!!!

I have too noticed a delay while browsing with firefox and more cpu usage when i load pages...


But i do get an error an lock-up when i try glxgears

When i start beryl i get this error

```

libGL warning: 3D driver claims to not support visual 0x4c
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
libGL warning: 3D driver claims to not support visual 0x4c

```

Is there something i can do???


Also i cannot get the water effects working

```
beryl: water: GL_ARB_fragment_program is missing
```

Unfortunately I think water effects are not supported by the driver at this time.  As for the page loading in FF, what happens if you try a different browser?  Does Opera cause an issue?  Opera isn't as much of a memory hog and it tends to render pages better, so it might be less load on the video card and reduce some of the lag.

---

### Post by riven0 on 2006-12-08
Thank you! This is awesome. Got beryl up and running without a hitch. Couldn't get it to work on my ati 9000 card. But on my ati 9200 it's wonderful. :) :KS

---

### Post by jtwadsworth on 2006-12-10
All this is great info, thanks.  I need help with my setup if you can...I am running an ATI Radeon 9800 Pro with fglrx drivers and beryl in edgy.  All runs great actually...

except:  when I log out and back in, the driver reverts back to MESA and the windows manager is all messed up.  Only a clean reboot will get it working again.  This is the same problem I had while running compiz in dapper...could get it to run great unless I logged out and back in.

Anyone have some ideas how to fix this?  On a side note, is AIGlx faster or slower than fglrx?

jtw

---

### Post by igknighted on 2006-12-11
> **jtwadsworth said:**
> All this is great info, thanks.  I need help with my setup if you can...I am running an ATI Radeon 9800 Pro with fglrx drivers and beryl in edgy.  All runs great actually...

except:  when I log out and back in, the driver reverts back to MESA and the windows manager is all messed up.  Only a clean reboot will get it working again.  This is the same problem I had while running compiz in dapper...could get it to run great unless I logged out and back in.

Anyone have some ideas how to fix this?  On a side note, is AIGlx faster or slower than fglrx?

jtw

This is very odd behaviour.  How are you loging out, with the GUI or with ctrl-alt-backspc?  The X driver shouldn't change just by logging out cause X shouldn't restart completely.  Are you running XGL/Beryl when this happens?  XGL will cause direct rendering to report as not enabled, could this be the issue?

---

### Post by jtwadsworth on 2006-12-11
I am logging out using the GUI...I am running Beryl/XGl at the time I log out.  How can I troubleshoot this?

jtw

---

### Post by igknighted on 2006-12-11
XGL does some screwy thing to the Ubuntu logout so this might be where your problem lies, so I might recommend giving AIGLX a stab.  It's supposed to be faster, but note that water effects will not work (if you are used to those).  It is also far less invasive, which is a major plus.

---

### Post by viz_e on 2006-12-12
After following the howto, I got beryl working. Unfortunately, it started to have problems after a couple of days. Here the problem is described:

[http://www.ubuntuforums.org/forumdisplay.php?f=132&page=3&order=desc]("http://www.ubuntuforums.org/forumdisplay.php?f=132&page=3&order=desc")

Any clue?

Thx!

---

### Post by linusr on 2006-12-13
i too face problem using beryl on edgy

> libGL warning: 3D driver claims to not support visual 0x4c

system crashes with scrambled display and had to restart

what could be the problem? Need help.

---

### Post by Treviño on 2006-12-14
That isn't the log of crash.. I mean that you posted is a common warning showed also if all goes ok... Maybe there's something else.

Try to look to your Xorg log file ;)

---

### Post by ANTDx1 on 2006-12-14
Reply to the original message: for some reason, some of the repositories are not working.  I am only getting a few of the emerald packages.  When I do apt-get update, the following happens on the repository you listed: 
Ign [http://www.beerorkid.com](http://www.beerorkid.com) edgy/main-edgy Packages
Ign [http://www.beerorkid.com](http://www.beerorkid.com) edgy/main-edgy Packages
Hit [http://www.beerorkid.com](http://www.beerorkid.com) edgy/main-edgy Packages
Hit [http://www.beerorkid.com](http://www.beerorkid.com) edgy/main-edgy Packages

It Ignores a few other portions of your repository, but it always ends up hitting them later on in the process.  However, when I try to get all the packages, it says it can't find emerald-core.  When I look for the packages in synaptics, it only lists beryl-plugin-data and emerald-themes.  That's not very useful without the main packages.

---

### Post by mt330404 on 2006-12-14
Hi, this is my first post. I am a VERY new Ubuntu Edgy user and I ran into some problems launching Beryl. After I installed AIGLX and Beryl, I typed beryl into the terminal to launch the program, and my computer went into a weird freeze-- the "taskbar" disappeared and I was unable to switch between windows on my screen. My only choice was to do a hard restart and try again from scratch, but every time I ended up in the same freezing situation.

System specs:
HP Pavilion ze1230 notebook
133-MHz SDRAM (PC133)
graphics & video chip: Integrated AGP, 3D embedded in VIA ProSavage.
CPU:   Technology code JA: AMD Athlon, up to 1.5 GHz.
Chip Set:   Technology code JA: Stepping A3 + VT8231.
256 MB ram

Here is the error message I get in terminal:

mike@mike-laptop:~$ beryl
XGL Absent, checking for NVIDIA
Nvidia absent, assuming AIGLX
libGL warning: 3D driver claims to not support visual 0x42
beryl: support for non power of two textures missing
beryl: failed to manage screen: 0
beryl: no manageable screens found on display :0,0
mike@mike-laptop:~$


Let me emphasize again that I am a very new user, so please don't be upset if I'm not as savvy with the linux lingo as everyone else. But, everyone has to start somewhere, we were all new at one point. So far I am LOVING Ubuntu Edgy, the interface and performance are awesome. Please let me know if you can help! It is greatly appreciated!!!!!

---

### Post by Steve S. on 2006-12-15
igknighted: Excellent thread!

I could never get this to work in Dapper.  Just upgraded to Edgy and ran this how to and it worked great...very simple.  Good job!

---

### Post by Knilch2000 on 2007-01-01
Thanks for this thread. 

I finally got beryl to work on my ATI 9800pro last night, using AIGLX!

I was under the impression that direct rendering wouldn't work on this card, and nearly at the point to give up AIGLX and use XGL. I always got "direct rendering: no" on glxinfo. I also noticed a warning about "AGP failed to initialize. Disabling the DRI." in /var/log/Xorg.0.log and something about a problem with apggart kernel module (which was loaded correctly at system boot though).

Well as I said at the time I was about to give up, I stumbled upon this site:
[http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy)
And there it says for ATI cards:
> 
Radeon 9200 owners
If direct rendering doesn't work and you see in your /var/log/Xorg.0.log:

 (WW) RADEON(0): [agp] AGP not available
 (EE) RADEON(0): [agp] AGP failed to initialize. Disabling the DRI.

You may need to add the following to your 'Section "Device"' block in your /etc/X11/xorg.conf to get Direct Rendering to work:

  Option "BusType" "PCI" 

(see [https://bugs.freedesktop.org/show_bug.cgi?id=1700](https://bugs.freedesktop.org/show_bug.cgi?id=1700) for details about this bug) 


Although I don't have a Readon9200, I noticed the error message in Xorg.0.log was the same as mine and just gave it a try. And, well, it worked! :D 

I now get "direct rendering: Yes" in glxinfo and beryl works perfectly :)

I also had to add some other options to the "Device" section of xorg.conf for the ati driver, because X refused to start using the standard conf (freezed the whole system). Especially the AGPSite and / or GARTsize options seemed to help when X (right now I'm not sure exactly which combination of options fixed this problem for me).

So if you have problems getting beryl / AIGLX to work on a ATI 9800 pro, try above fix or some of the options of my xorg.conf :) 

```

Section "Module"
...  
        Load    "dbe"
        Load    "dri"
        Load    "glx"
...
EndSection


Section "Device"
        Identifier      "ATI R350 Radeon 9800 Pro"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option "AGPMode" "8"
        Option "AGPSize" "64"
#        Option "AGPFastWrite" "on"  #causes X freeze
        Option "AccelMethod" "XAA"
        Option "ColorTiling" "on"
        Option "DynamicClocks" "on"
        Option "RenderAccel" "true"
        Option "TripleBuffer" "true"
        Option "DRI" "true"
        Option "EnablePageFlip" "true"
        Option "EnableDepthMoves" "true"
        Option "XAANoOffscreenPixmaps"
        Option "BusType" "PCI" #!!! neccessary for direct rendering
#       Option "GARTSize" "128"
EndSection

...

Section "ServerLayout"
        Option          "AIGLX"         "true"
...
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

```

:)

---

### Post by songochain on 2007-01-05
Hi, i'm trying to run beryl+aiglx with a radeon mobility 9700 but i cant. Beryl+xgl works fine but i get a slow performance...
I've installed all i need (i guest): xserver-xorg-driver-ati, beryl, xorg modified... but it doesnt work :( Also, if i use ati module on section device, laptop fan sets to 100% (fix??)
Here's my xorg.conf:
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
	Option	"AIGLX"	"true"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
	Load  "dbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "es"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Driver      "ati"
	Option "XAANoOffscreenPixmaps"
	Option "AllowGLXWithComposite" "true"
	Option "EnablePageFlip" "true"

# This two lines are (presumably) needed to prevent fonts from being scrambled
        Option  "XaaNoScanlineImageWriteRect" "true"
        Option  "XaaNoScanlineCPUToScreenColorExpandFill" "true"
#Optimized values (changed from driver default)
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "on" #Faster than default (off)
	Option		"SWcursor" "off" #Faster than default (on)
	Option		"EnablePageFlip" "on" #Faster than default (off)
	Option		"AccelMethod" "EXA" # or XAA, EXA, XAA more stable, XAA is deafult
	Option		"DynamicClocks" "on"
	Option		"BIOSHotkeys"   "on"
	Option		"AGPSize" "32" # default: 8
	Option		"EnableDepthMoves" "true"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "ati"
	Option "XAANoOffscreenPixmaps"
	Option "AllowGLXWithComposite" "true"
	Option "EnablePageFlip" "true"

# This two lines are (presumably) needed to prevent fonts from being scrambled
        Option  "XaaNoScanlineImageWriteRect" "true"
        Option  "XaaNoScanlineCPUToScreenColorExpandFill" "true"
	#Optimized values (changed from driver default)
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "on" #Faster than default (off)
	Option		"SWcursor" "off" #Faster than default (on)
	Option		"EnablePageFlip" "on" #Faster than default (off)
	Option		"AccelMethod" "EXA" # or XAA, EXA, XAA more stable, XAA is deafult
	Option		"DynamicClocks" "on"
	Option		"BIOSHotkeys"   "on"
	Option		"AGPSize" "32" # default: 8
	Option		"EnableDepthMoves" "true"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

```

Thanks!

---

### Post by admiralawesome on 2007-01-08
On a fresh install of Kubuntu Edgy, after getting all the latest updates, I followed through this how-to until the part about editing the apt sources.  At that point I switched over to this how-to: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX"), and it works almost perfectly with my Mobility 9600.  I commented out the xorg.conf lines for AGPFastWrite and AGPMode, though to be honest, I didn't test things out with them enabled first.  The only real problem I have is with video playback and some of the Beryl effects.  Playing the video as normal works fine.  However, video playback is blank or garbage within the Beryl Alt+Tab window switcher and on the faces of the 3D cube when it's being rotated with the mouse.  Video playback seems to work fine with the Scale effect.  It'd be great to get these minor video playback issues fixed, but it's not a big deal.  I'd never used the "radeon" driver before, and I'm really surprised with how well it performs.  Thanks for the how-to.

---

### Post by Cirdan7 on 2007-01-09
It says I don't have the GLibC 2.4 packages for osme reason. Yes, I am running edgy.

beryl-manager: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by beryl-manager)

EDIT--------------------

Ok, I chagned all of the dapper's in the sources.list to edgy and installed libc6. That fixed that, but when I run beryl none of the window borders show up. What am I missing?

---

### Post by songochain on 2007-01-09
> **admiralawesome said:**
> On a fresh install of Kubuntu Edgy, after getting all the latest updates, I followed through this how-to until the part about editing the apt sources.  At that point I switched over to this how-to: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX"), and it works almost perfectly with my Mobility 9600.  I commented out the xorg.conf lines for AGPFastWrite and AGPMode, though to be honest, I didn't test things out with them enabled first.  The only real problem I have is with video playback and some of the Beryl effects.  Playing the video as normal works fine.  However, video playback is blank or garbage within the Beryl Alt+Tab window switcher and on the faces of the 3D cube when it's being rotated with the mouse.  Video playback seems to work fine with the Scale effect.  It'd be great to get these minor video playback issues fixed, but it's not a big deal.  I'd never used the "radeon" driver before, and I'm really surprised with how well it performs.  Thanks for the how-to.

Me too dude, but beryl doesnt start if i use aiglx with open radeon driver (also 100% cpu fan) so i've to use xgl :(

---

### Post by lennox on 2007-01-10
> **songochain said:**
> Hi, i'm trying to run beryl+aiglx with a radeon mobility 9700 but i cant. Beryl+xgl works fine but i get a slow performance...
I've installed all i need (i guest): xserver-xorg-driver-ati, beryl, xorg modified... but it doesnt work :( Also, if i use ati module on section device, laptop fan sets to 100% (fix??)
Here's my xorg.conf:
```

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Driver      "ati"
	Option "XAANoOffscreenPixmaps"
	Option "AllowGLXWithComposite" "true"
	Option "EnablePageFlip" "true"

# This two lines are (presumably) needed to prevent fonts from being scrambled
        Option  "XaaNoScanlineImageWriteRect" "true"
        Option  "XaaNoScanlineCPUToScreenColorExpandFill" "true"
#Optimized values (changed from driver default)
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "on" #Faster than default (off)
	Option		"SWcursor" "off" #Faster than default (on)
	Option		"EnablePageFlip" "on" #Faster than default (off)
	Option		"AccelMethod" "EXA" # or XAA, EXA, XAA more stable, XAA is deafult
	Option		"DynamicClocks" "on"
	Option		"BIOSHotkeys"   "on"
	Option		"AGPSize" "32" # default: 8
	Option		"EnableDepthMoves" "true"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "ati"
	Option "XAANoOffscreenPixmaps"
	Option "AllowGLXWithComposite" "true"
	Option "EnablePageFlip" "true"

# This two lines are (presumably) needed to prevent fonts from being scrambled
        Option  "XaaNoScanlineImageWriteRect" "true"
        Option  "XaaNoScanlineCPUToScreenColorExpandFill" "true"
	#Optimized values (changed from driver default)
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "on" #Faster than default (off)
	Option		"SWcursor" "off" #Faster than default (on)
	Option		"EnablePageFlip" "on" #Faster than default (off)
	Option		"AccelMethod" "EXA" # or XAA, EXA, XAA more stable, XAA is deafult
	Option		"DynamicClocks" "on"
	Option		"BIOSHotkeys"   "on"
	Option		"AGPSize" "32" # default: 8
	Option		"EnableDepthMoves" "true"
	BusID       "PCI:1:0:0"
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

```


Hey, your xorg.conf looks pretty messed up.
I suggest backing up your xorg.conf, then do
```

sudo dpkg-reconfigure xserver-xorg

```
and so start with a fresh one.
First, you need the "radeon" driver, not the "ati".
You can look at your old xorg.conf and copy the stuff you KNOW you need to the new one.
There are plenty of HOWTOs around that tell you how to do the rest (at least on edgy), I followed a German one, so I guess that wouldn't help.

---

### Post by songochain on 2007-01-10
Also i probed with radeon but same problem. I've cleaned my xorg.conf and nothing. I think it's better wait for fglrx supports aiglx

---

### Post by kadajjj on 2007-02-10
I have 9800 pro and computer hangs on when beryl is Checking Screen 0 ...
Anyone have idea why its hangs?

---

### Post by enemie on 2007-03-28
Thx to all! With this  thread i got my ATI Radeon 9800 PRO running with beryl

---

### Post by justin13 on 2007-06-13
wth the repo is dead!

---

