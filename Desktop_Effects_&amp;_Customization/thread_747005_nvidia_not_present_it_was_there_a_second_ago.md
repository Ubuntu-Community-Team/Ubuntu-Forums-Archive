---
title: "nvidia not present? it was there a second ago"
date: 2008-04-06
forum: Desktop Effects &amp; Customization
---

### Post by Paraphysicist on 2008-04-06
I'm new to ubuntu, just installed it yesterday.  I got compiz fusion working, and everything worked great right up until I installed this skydome: [http://lottalinuxlinks.com/wallpapers/skydome_doom3_1024x512.png](http://lottalinuxlinks.com/wallpapers/skydome_doom3_1024x512.png)

I don't know if it was that image or not, but everything stopped working.  I am now unable to enable custom settings in the Appearance Preferences window.  When I type in compiz into the terminal I get this output:

slippy@Sleepy-Desktop:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Not a JPEG file: starts with 0x89 0x50

At first I was missing Xgl so I installed it.  

I tried reinstalling the nvidia driver, but I got the same message.  Btw it's an 8600 GT video card.  I'm at a loss of what to do next.  Should I reinstall Ubuntu?  Any advice would be greatly appreciated.

---

### Post by Paraphysicist on 2008-04-06
bump

---

### Post by mrmiserable on 2008-04-06
have you tried to turn of skydome 

also if compiz was working before sometimes plugins crash compiz 

i hope you reinstalled driver correct and did you install xserver-xgl after the crash

also did you turn on jpeg plugin

---

### Post by Paraphysicist on 2008-04-06
mrmiserable, thank you for the reply.  I turned off skydome but it didn't help.  Java and flash are the only plugins I installed. 

I may not have reinstalled the driver right, what is the best way to install it?  I will try to install xserver-xgl.  I don't thing I installed a jpeg plugin, where would I find it?

Thanks

edit: I installed xserver-xgl but it says I already have the newest version

---

### Post by mrmiserable on 2008-04-06
ok a bit confused did you install ccsm (compizconfig-settings-manager)

do not install xgl it is usually only needed for ati cards 

how did you install your card originally is probably the best way if not you could try envy (i have never used it so i cannot tell if it is good)

also post output from terminal 

glxinfo | grep direct

jpeg plugin is in ccsm under images tick box

---

### Post by Paraphysicist on 2008-04-06
I installed ccsm and compiz was working well until I added that skydome.

I will remove xgl.  What I did for my video card was go to system>administration>restricted drivers manager and enabled the nvidia accelerated graphics driver (latest cards)

I went to tick the box on the jpeg plugin in ccsm and it was ticked.

Here is the terminal output:

slippy@Sleepy-Desktop:~$ glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)


edit: how do I remove xgl?

---

### Post by mrmiserable on 2008-04-06
ok  to remove xgl either open synaptic and remove by searching for it 

or open a terminal and code

sudo apt-get remove xserver-xgl

no dri means no compiz 

also if this is a fresh install eg: yesterday you could just reinstall so you have clean system and start again  because you said you reinstalled driver and maybe there is conflict now 

just an option or try to turn on restricted driver again eg turn off turn on maybe it will reconfigure to be correct

try these and if no luck get back and let me know

---

### Post by Paraphysicist on 2008-04-06
I removed xgl and reinstalled the restricted driver.  I also tried to reinstall compiz.  Now it works for about 10 seconds whereas before it was about 2.  I will probably just reinstall ubuntu, I just wish I knew why that skydome messed everything up so I can avoid the mistake later.

Edit: I typed in compiz into the terminal and now it suddenly works

slippy@Sleepy-Desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0402 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
sudo apt-get install compiz

---

### Post by Paraphysicist on 2008-04-06
I have the cube and the advanced graphics, but now I don't have that border on the top of each window- the minimize, maximize, close buttons are all gone.  I also can't drag windows.  I'll try to post a pic

---

### Post by mrmiserable on 2008-04-06
i had same problem when i used nvidia driver in xorg.conf but got window borders with nv driver

but if you got it to work before perhaps it is just install emerald-themes
it has a different name now like libdecoration0 
check in synaptic under compiz

if you need more help just ask

edit also in ccsm under window decorations-command add 
emerald --replace
this will start emerald everytime compiz starts it should do it by default but sometimes it does not

also the compiz forum is a good place for info this thread is for nvidia setup 

[http://forum.compiz-fusion.org/showthread.php?t=1682](http://forum.compiz-fusion.org/showthread.php?t=1682)

---

### Post by Paraphysicist on 2008-04-06
I uninstalled then reinstalled emerald, and everything came back fine.  I don't know how it happened or what I pressed in the ccsm, but it shifted the entire screen.  I dunno how to explain it, but if the desktop is a clock, and theres a button at 6:00, you have to move the cursor to 3:00 to press it.  So I just got fed up and reinstalled the OS.  

Just for the hell of it, I'm going to add that skydome again and see if it messes anything up.

Thank you for all of your help through this :guitar:

---

### Post by Paraphysicist on 2008-04-06
It messed everything up again, but deleting the dome and restarting the computer fixed it.  I found the same skydome from here: [http://fc05.deviantart.com/fs20/f/2007/246/7/e/Doom_Skydome_by_invisible__kid.png](http://fc05.deviantart.com/fs20/f/2007/246/7/e/Doom_Skydome_by_invisible__kid.png) , installed it and it works fine.

---

### Post by mrmiserable on 2008-04-07
oh joy i thought you was a masochist

glad it's fixed now go and mess about with this thread it will give you more plugins for compiz

[http://forum.compiz-fusion.org/showthread.php?t=5303](http://forum.compiz-fusion.org/showthread.php?t=5303)

good luck

---

