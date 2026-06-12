---
title: "Hardware volume buttons  no longer work (odd one)"
date: 2007-07-16
forum: Dell  Ubuntu Support
---

### Post by writingsama on 2007-07-16
here's my story.  I ditched Windows in favor of Ubuntu.  However, as we all know, there is no good voice recognition for linux.  So, having frustration with VMWare, I turned to VirtualBox.

I have a Dell Inspiron 6400 w/ Core 2 Duo 1.83GHz,1 gig of RAM, 160gb HD, Ubuntu 7.04 feisty with 2.16.20-lowlatency kernel installed.

to get Ubuntu to install properly, I used the install scripts from [http://mylittleubuntuguide.com](http://mylittleubuntuguide.com).  Ever since I installed it, the volume buttons have worked perfectly.then I made threechanges and they stopped working:

one.  I downgraded VirtualBox to 1.3.8 to get Dragon NaturallySpeaking working 
2.  I added multimedia source control and volume control to the system -- preferences menu, and used them to select and set up microphone capture
three.  I installed the aforementioned 2.16.20-lowlatency package, and have been booting off it.

I went to all this trouble because I have severe tendinitis and I need some way of inputting text -- speech is just about the only way to do it.  It is now all working properly, finally.  But!  My volume control buttons on my laptop no longer work.  This is more than a minor inconvenience: the aforementioned tendinitis makes any extra mouse work difficult.

I've checked, and the keyboard shortcuts are still set correctly.when I first boot, the volume up and down buttons pull up the on-screen volume indicator, but don't have any actual effect on the volume.if I turn the volume all the way down, the onscreen indicator indicates that it is muted.  I then can only use the volume down or mute buttons to pull the onscreen indicator up: the volume up button does nothing!

Is there any way that I can get the volume buttons working again?

I thank you very much for your replies!

---

### Post by joe.turion64x2 on 2007-07-16
Open a terminal and run *alsamixer*, does it start?

---

### Post by markclewis1 on 2007-07-17
I too am having the same problem with the hardware sound buttons on my Dell Inspiron 1505.  I have re-loaded Ubuntu Feisty a few times over the last few weeks for various trial and error reasons, and the volume buttons have always worked perfectly until this last time.  I ran alsamixer in terminal and it did come up.  Does not change the fact that Feisty is not recognizing this part of my hardware.  Help would be appreciated....

Mark

---

### Post by neptho on 2007-07-17
It could be several things, but here's a quick and easy hack job to get it all working:

```
%sudo apt-get install xmodmap
```
Edit ~/.xmodmaprc
```
keycode 160 = XF86AudioMute
keycode 174 = XF86AudioLowerVolume
keycode 176 = XF86AudioRaiseVolume
keycode 162 = XF86AudioPlay
keycode 164 = XF86AudioStop
keycode 144 = XF86AudioPrev
keycode 153 = XF86AudioNext
keycode 168 = XF86AudioMedia
```

Create a new startup item, and run 'xmodmap /home/yourlogin/.xmodmaprc'.

---

### Post by writingsama on 2007-07-17
thanks, but this still does not fix my problem :-(
I think its something in Gnome...

---

### Post by neptho on 2007-07-17
> **writingsama said:**
> thanks, but this still does not fix my problem :-(
I think its something in Gnome...

Ok, so it's not firing off the programs assigned to your keys.  If you want to cheat even further, you can install 'keytouch', and have it define your keys *and* what programs to run for each key.  A standard dell media keyboard will work, but if you install the keytouch-editor, you can create a custom setup for your keyboard.

---

### Post by strabes on 2007-07-18
I also recommend keytouch for gnome. In KDE (kubuntu) most of these types of buttons work out of the box.

---

### Post by writingsama on 2007-07-21
So, I dig a bit of digging..

For some reason the volume keys (assigned in System->Preferences->Keyboard Shortcuts) are changing my MICROPHONE VOLUME.

??? How can I change this?

---

### Post by joe.turion64x2 on 2007-07-21
> **writingsama said:**
> So, I dig a bit of digging..

For some reason the volume keys (assigned in System->Preferences->Keyboard Shortcuts) are changing my MICROPHONE VOLUME.

??? How can I change this?
Right click the speaker in the notification bar (next to the clock), click Preferences and select the Device and Track to control.

Joe.

---

### Post by AtrejuT on 2007-08-10
I have the same problem, but assigning the correct device does not help. The hardware buttons still change microphone...
(HDA Intel, alsa 1.0.14)

---

### Post by ethos101 on 2007-08-11
I'm having a similar problem on my desktop.  I have a labtec keyboard with volume buttons on it.  It worked great out of the box.  Now it just moves the slider up and down but the volume doesn't change unless I manually move the alsamixer master slider.  I don't know what I did for it to quit working.  It may have something to do with me trying to get sound recorder to record from the mic, which was unsuccessful.

Fixed....  system ->preferences ->sounds then adjusted mixer tracks or something.  It's really unclear what I did but it works now.

---

### Post by AtrejuT on 2007-08-11
really funny: setting the 'prefered track' via the little icon in the notification area didn't help at all. but doing it as you suggested via system-preferences-sound did the job... thanks!

---

### Post by AndyQ on 2007-08-19
> **AtrejuT said:**
> really funny: setting the 'prefered track' via the little icon in the notification area didn't help at all. but doing it as you suggested via system-preferences-sound did the job... thanks!

Same here - thanks! it was driving me mad!

---

### Post by malachias on 2007-11-21
thanks so much! i too had the mysterious volume controls controlling the wrong sliders... and your solution worked, finally!

---

### Post by terklotron on 2007-11-24
> **ethos101 said:**
> 

Fixed....  system ->preferences ->sounds then adjusted mixer tracks or something.  It's really unclear what I did but it works now.

GREAT!!! Thanx.
Had the same problem on my Inspiron 6000. Had no idea what to do, but then.... wuhuuu.
I just sat the "default mixer typer" (device= alsa mixer) to MASTER, and voila.

Peace=D>

---

### Post by StefAndrew on 2008-02-05
I had a similar problem.  I just didn't realize I had cause it myself.  I had selected all the options to use with the volume controls and could figure out why all of them were moving at the same time when I only wanted to control the master volume.  This post made me realize exactly what I had done by selecting them all.

Thanks for the help everyone.

---

