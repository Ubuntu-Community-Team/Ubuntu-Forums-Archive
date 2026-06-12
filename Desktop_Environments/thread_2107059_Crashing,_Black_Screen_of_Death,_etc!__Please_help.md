---
title: "Crashing, Black Screen of Death, etc!  Please help!"
date: 2013-01-20
forum: Desktop Environments
---

### Post by psyllex on 2013-01-20
I installed Ubuntu 12.10 on my desktop about 4 weeks ago.  Ever since then I've had to reinstall it 5 times.  The first time Unity crashed and I couldn't even get to a terminal...just the an non-right-clickable arrow and the background.  Then it crashed when I had the OpenGL Cairo dock and didn't recover.  Then I downloaded wine and W.o.W and it did the black screen of death thing.  Lastly it did the black screen of death and all I did was move from flgrx (not sure if that's the proper name) to the proprietary drivers for AMD/ATI graphics.  So what am I doing wrong?  other than installing proprietary drivers I didn't do anything really crazy do my machine...downloaded GCC, G++, emacs, some monitoring tools, apache2, mysql, your general lamp stuff, and openssh and ssl.  Can someone please help out?

---

### Post by bogan on 2013-01-21
Hi!, **psyllex**,

Here is my standard response to queries like yours that ask for help, but give no essential info:> Please Post details of what you actually experience when you try to boot, and what you have tried to solve things;

EG,. how far does it get?,
what do you see?
What response you get to keystrokes? - such as 'Crtl+Alt+F1', 'Crtl+Alt+Del', or 'Shift'[ the later during boot sequence].

If you get a grub menu: Have you tried:
Booting to recovery?
Editing the grubmenu script?, eg to put in 'nomodeset'

Or tried Booting from a LiveCD/USB?

Please also Post details of your setup: computer make and model, CPU, integrated Graphics?, GPU,video card, memory, and how Ubuntu/Lubuntu is installed, ie with 'wubi' or direct, and if dual with Windows.[ If the later, does it work??]

Also please Post the output of the following, if you can get to a terminal [ or tty].```
uname -ar
lspci -nnk | grep -iA3 VGA
/usr/lib/nux/unity_support_test -p
```Copy/Paste the command and output to a 'New Reply' edit box. highlight it and press the '#' icon in the toolbar at the top of the edit box.Chao,** bogan**.

---

### Post by psyllex on 2013-01-21
> **bogan said:**
> Hi!, **psyllex**,

Here is my standard response to queries like yours that ask for help, but give no essential info:Chao,** bogan**.

I've attempted about everything I could thing of analogous to ctrl+alt+delete.  And as I stated what I had to do was reinstall, it isn't a corrupted installation device because I re-downloaded the .iso each time I reinstalled just to be sure.  I've seen other posts about issues with proprietary graphics drivers.  I've attempted a few and I think installing the ATI drivers actually may have caused a crash one of the times.  The other times I have no idea what happened.  I could hear my computer responding to keystrokes or other commands I could try from just the desktop like opening the terminal but I wasn't typing correctly (since I couldn't see) so I just gave up and reinstalled.  I will get the results of that command when I get home to my machine.

---

### Post by psyllex on 2013-01-22
alright response from your command:

```
Linux psy-HP 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

00:01.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI BeaverCreek [Mobility Radeon HD 6620G] [1002:9641]
	Subsystem: Hewlett-Packard Company Device [103c:358b]
	Kernel driver in use: radeon
	Kernel modules: radeon
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI BeaverCreek [Mobility Radeon HD 6620G] [1002:9641]
	Subsystem: Hewlett-Packard Company Device [103c:358b]
	Kernel driver in use: radeon
	Kernel modules: radeon
psy@psy-HP:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   X.Org
OpenGL renderer string: Gallium 0.4 on AMD SUMO
OpenGL version string:  2.1 Mesa 9.0

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```

For the time being I installed GNOME.  That has solved the issue (I believe and hope) for the time being until I can get it sorted out.  It may be an issue with my computer though...the bios got wiped out it looks; or at least that is what it alerted me to when I booted up one time, that HP bios has been deleted alert alert!  Unfortunately I wasn't paying super close attention to it.  I could go back to 12.04 L.T.S. that worked like a well oiled machine...but there was some graphical elements to 12.10 that I like.  Unfortunately I don't have that much time to mess around with it.  I did a :**apt-get cache search** on fglrx and essentially tried to install what look like my drivers (Radeon).  My machine would still go black, then I would reboot and try the next one...and so on.  I had it working when I installed only the fglrx drivers for awhile but then I did some tinkering with compiz and that caused it to go back to the black screen on reboot or when waking up from sleep mode.  

I've tried various solutions (which I need to write down from now on since as you said I don't give any information to go off).  I'll keep searching through the forums to see if there's any solutions, keep track of them and then report them here.  Unless you see something in those results that would lend me a suggestion which I would truly appreciate.

---

### Post by bogan on 2013-01-22
HI!, **psyllex**,

I do not understand why lspci shows two identical "[AMD] nee ATI BeaverCreek [Mobility Radeon HD 6620G] " VGA adapters, both using the radeon driver; especially as they are the Mobility version, that suggests you are using a laptop, hardly likely to have two video cards.

Whilst the output from the unity test suggests the Xorg used is from the nouveau driver.

I would be inclined, if the current situation is not acceptable - and I am assuming that you are having to log in to a Gnome session, as Unity does not work correctly if you log in to 'ubuntu' - to try two things:

First run:```
sudo apt-get install --reinstall ubuntu-desktop
sudo reboot
```Then log in to ubuntu and see if things are any different.

Second, my limited knowledge of AMD video cards is that the GPU you have - HD6620G - does not like the fglrx driver and the 12.10 Xorg server and that the correct driver is that shown as in use - radeon - but the unity_test suggests it is not correctly installed, so try: ```
sudo apt-get install --reinstall xserver-xorg-video-radeon
sudo reboot
```.Then run again```
/usr/lib/nux/unity_support_test -p
``` and compare results with the previous output.

If anyone reading this has more experience with AMD cards and thinks otherwise, please come in.

**Edit: **It maybe that you need to do a more complex purge of the remaining elements of the fglrx driver, if you did not do so.

Chao!, **bogan.**

---

### Post by psyllex on 2013-01-29
> **bogan said:**
> HI!,Then run again```
/usr/lib/nux/unity_support_test -p
``` and compare results with the previous output.

If anyone reading this has more experience with AMD cards and thinks otherwise, please come in.

**Edit: **It maybe that you need to do a more complex purge of the remaining elements of the fglrx driver, if you did not do so.

Chao!, **bogan.**

I ran the test again and here are the results:
```
OpenGL vendor string:   X.Org
OpenGL renderer string: Gallium 0.4 on AMD SUMO
OpenGL version string:  2.1 Mesa 8.0.4

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```

I still have the problem that when I actually set my PC to sleep, it won't recover for wakeup.  I haven't found a solution yet so if anyone has any ideas...I'm all ears.  I have to have my PC running at all times, only dimming the screen.  If it goes to sleep....it will need a complete reboot.
:confused:

---

### Post by bogan on 2013-01-30
Hi!, **psyllex**,

I think the failure to wake correctly from Sleep is a different issue and you would be better off to Post a separate Thread, if you have not already done so.

If the BSOD is no longer a problem, please mark this thread as 'Solved'; or do you still get one if you log-in to ubuntu??

Chao!, **bogan.**

---

### Post by psyllex on 2013-01-30
No, I only get that when I put the screen to sleep.  Or shut my laptop....which then I can see the backlight on but can't get the display to come up.  So I'll start a new thread.  Thanks for all the help.

---

