---
title: "Dual screen + ATI fglrx + Xgl + Compiz Fusion"
date: 2007-07-28
forum: Desktop Effects &amp; Customization
---

### Post by TheRealRockeT on 2007-07-28
Hi,

I have a Radeon X800 pro, connected to 2 19" monitors both at 1280x1024. I'm trying to get Compiz Fusion working on both monitors.

I have followed the HOWTO at [http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385) which gives me nice desktop effects for single monitor. Its very beautiful and impressive!

I'm now trying to work out how to get Compiz working with a dual monitor fglrx setup. I need to get xorg.conf set up for Xgl, which it seems is tricky.

I currently set my desktop up as a single, big screen. It works in a normal GNOME session.

```
Section "ServerLayout"
        Identifier     "Default Layout"
        Screen         "Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection

(skipped input sections etc.)

Section "Monitor"
        Identifier   "SyncMaster[0]"
        Option      "DPMS"
EndSection

Section "Device"
        Identifier  "ATI Technologies Inc R420 JI [Radeon X800PRO][0]"
        Driver      "fglrx"
        Option      "DesktopSetup" "horizontal,reverse"
        Option      "Capabilities" "0x00000800"
        Option      "PairModes" "1280x1024+1280x1024"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Screen[0]"
        Device     "ATI Technologies Inc R420 JI [Radeon X800PRO][0]"
        Monitor    "SyncMaster[0]"
        DefaultDepth     24
        SubSection "Display"
                Depth     24
                Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "
720x400" "640x480"
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection

```

With this config, fglrxinfo gives me:

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 PRO
OpenGL version string: 2.0.6334 (8.34.8)
```

When I try to log into the "GNOME with XGL" session, I get the following in ~/.xsession-errors

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "rocket"
/etc/gdm/Xsession: Beginning session setup...

Fatal server error:
no screens found

(gnome-session:5991): Gtk-WARNING **: cannot open display:  
```

Please advise of other logs, config etc. I can post to help

(the config works fine for normal GNOME session)

---

### Post by mr-bean on 2007-08-04
I've got exactly the same situation.  Compiz-fusion is running well if only one screen is used. (both monitors show the same image).
If I enable "big desktop", it runs if I login using non XGL.
If I try to login to an XGL session with "Big Desktop" enabled, I get:

Fatal error
No screens found

Looks like you not had any help so far.
I've been looking for 3 days now, and am getting nowhere fast.
I hosed my install a few time too.  :-)

So it's either 1 screen with cool effects, or 2 screens and no eye candy.
Let me know if you have made any progress on this...
Regards...

Mr-Bean...

---

### Post by ManOnOneWheel on 2007-08-12
Arg! I'm having the same problem as both of you. CF works great in non-XGL dual screen and in XGL single screen, but dual screen SGL gives me the same errorI have an ATA X300, and I'm trying to get it to work on my laptop screen which is 1024x768 and my external monitor ad 1440x900. If anyone has any help for us please tell!

My xorg.conf looks very similar to RealRocket's except my resolution values are different.

I can't wait till I get my new computer with an nVidia card, no more fglrx!

---

### Post by Mongo5000 on 2007-08-13
Just wondering if dual monitors on an nvidia card work with Beryl?  I really want the pretty eye candy but if its not going to work with dual monitors, then i'll stick with a single monitor.

---

### Post by bob27 on 2007-08-19
Same problem here too. Anything we can do to fix this or are we just stuck? Also, will this be fixed in Gusty?

---

### Post by blairboy362 on 2007-08-19
Hi,

I'm having the same problem as those above. Has anyone found a solution for this yet?

---

### Post by digital_exhaust on 2007-08-19
Same issues here... 

P4 3g, 1g ram, X1950pro 256m AGP and 2x Viewsonic VA1912wb's and no Compiz love for me either.... in fact I can't even get my resolution where it needs to be under Big Desktop... 2880x900... won't do it, and every time I've tried I have managed to completely bork my install..... 

I think we all may be out of luck... hopefully some of these issues will be worked out in Gusty... I need my dual screens and I really like Compiz... not a deal breaker or anything, but it sure would be nice...

---

### Post by Mongo5000 on 2007-08-19
I went out and replaced my ati x1600 with a similiar nvidia card.  All problems solved in record time.

I got dual monitors working great, beryl going like crazy and now can finally enjoy my ubuntu instead of getting it all to work.

Well worth the price of a new vid card if you ask me.

---

### Post by bob27 on 2007-08-20
Strange that nVidia solved your problem. I have a friend with an nVidia (6200 i think) and he has the same problem. I thought it was a general dual monitor + Compiz issue.

---

### Post by blairboy362 on 2007-08-20
No - nVidia have solved it. 2 of my friends have nvidia cards and they both have dual screens with Beryl/Compiz working. But they don't use Xgl. The nVidia drivers supply Compiz with the necessary API, I believe.

---

### Post by Mongo5000 on 2007-08-22
I just used the restricted drivers and poof, working like a charm.

I got a GF7600 GS.

---

### Post by blairboy362 on 2007-08-22
Yeah. Getting an nVidia card appears to be the way forward. Not very good for ATI at all. Though, one could argue we are in a niche market

---

### Post by d0rp on 2007-08-23
I am having the same problem, I can't seem to get the eye candy working with my dual headed ATI card.

However, since my motherboard has on-board graphics (I think Intel), I'm wondering if it would be possible to run one monitor off the ATI card and the other off the on-board graphics and then get the fancy eye candy to work that way. 

Any suggestions before I start messing with things?

---

### Post by damrodd on 2007-09-13
bump

---

### Post by dark_harmonics on 2007-09-13
I hate to be the bearer of bad news but i think that XGL will not redner the second screen which is why you get dual-head to work but the second screen just has an X when you move you mouse over it. I did get big desktop to work but not dual head :(. 

My suggestion is to wait and see what comes from the changes that will occur from the ATI/AMD recent events.

I have already messed up a computer config trying to figure this one out... 

I really think we just need to be rid of XGL and finally get full ATI overlay to work.

check out this thread [http://ubuntuforums.org/showthread.php?t=549732](http://ubuntuforums.org/showthread.php?t=549732)

---

### Post by marco27 on 2007-09-13
Under ati/xgl one way is to run 2 xgl sessions.  You end up with a separate cube running on each screen.  

Follow this thread for the startxgl script:
[http://ubuntuforums.org/showthread.php?t=378281](http://ubuntuforums.org/showthread.php?t=378281)

---

### Post by CowzRule on 2007-09-14
I believe you are limited by the fglrx drivers to a screen resolution of 1024x768 when running "Bigdesktop". With 2 monitors, that gives you a desktop size of 2048x768. I used to have the same x800pro and I was running that resolution with Beryl just fine.
Also, if the only "3d" thing your going to be doing is running Compiz-Fusion, you don't need to use the fglrx drivers. The built in open source Radeon drivers supports the x800pro which allows you to use AIGLX instead of XGL.
I've attached my old xorg.conf files for both drivers running dual monitors. I edited them with Open Office so that I could highlight the info that relates to dual monitors.

---

### Post by dark_harmonics on 2007-09-16
> **marco27 said:**
> Under ati/xgl one way is to run 2 xgl sessions.  You end up with a separate cube running on each screen.  

Follow this thread for the startxgl script:
[http://ubuntuforums.org/showthread.php?t=378281](http://ubuntuforums.org/showthread.php?t=378281)


This totally worked for me! It does run 2 completely seperate sessions but it gave me functionality until the native ati drivers are released. Thanks alot!

---

### Post by Mavtech on 2007-09-16
Isn't the Extension part of xorg suppose have "Enabled" in it?  Like this:

```
Section "Extensions"
        Option      "Composite" "Enabled"
EndSection
```

This worked for me when I was getting the "Composite Extension is not available" error.


I am working with Compiz on my laptop with an ATI X1400.  I got wobbly windows to work in the XGL session.  But, cannot get the cube to work.

---

### Post by james1030 on 2007-12-16
whats up,
well it looks like i have the same issues as you all.
X800pro
2x19" (1440x900)
i can get compiz working great as a mirror with just the proprietary drivers, but when i try to mess with the Xorg, and get big desktop working properly, compiz shuts off.
thinking of just going with an Nvidia. any suggestions?

---

### Post by kesman on 2007-12-17
Have you guys tried the newest fglrx driver? It's supposed to support AIGLX so no more XGL-stuff is needed for compiz to work with ATI cards.
As soon as I get home I'll give this thread a try with my laptop and lcd-tv which I haven't got working so far :S

---

