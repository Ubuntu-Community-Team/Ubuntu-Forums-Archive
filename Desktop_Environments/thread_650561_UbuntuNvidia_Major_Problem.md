---
title: "Ubuntu/Nvidia Major Problem"
date: 2007-12-26
forum: Desktop Environments
---

### Post by MrTripi on 2007-12-26
Ok, I know I'm new to Linux and all, but this is probably my third time hitting a brick wall within the span of one semester where I'll probably need to reformat my entire hard-drive because the unbreakable OS keeps breaking.

The Story:

First of all, I have an Nvidia Geforce FX GO5200 graphic card.  I know it's not top of the line anymore, it's decent though; does what it needs to do.  I have an Inspiron 5150 notebook, I don't know if that helps anyone in here identify my numerous problems.

1) Everytime-everytime!- I installl Ubuntu i have the same problem with this graphic card.  After a while, the windows will only display black spaces.  I'll need to hit ctl + alt + f2 then then ctl + alt + f8 in order to see something in my windows again, this doesn't always work though-and more often than not they'll go back to being back when I minimize and open them again.  It pretty much gets to the point where if I have more than one window open they'll all turn black so I have to minimize all but one of them in order to see something.  This gets tiresome as you may have guessed-so I assumed it was a graphic problem and went on the hunt for a new/better driver.  

So I search Symantec, I try the Nvidia Legacy Drivers, no good.  I tried the Nvidia GLS(I think it's GLS) drivers, no good.  I tried the Nvidia GLS New drivers, still no good.  Finally I decide to search online for better/unsupported drivers.  

I tried theese ----->[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) the version 1.69 drivers.  So alright, awesome.  I start installing them, I get all these warnings about Nvidia needing to compile it's own kernel, but it seems to work.  I restart the computer and I get low resolution because the computer can no longer detect what type of card I have.

I immediatey reinstall the old drivers (or so I think, again I'm a total noob at this Linux thing) then go about my business.  Unfortunately I now realize that 

a) I can no longer use the extra visual effects which fail to load
b) Second Life no longer can open a window
c) My favorite, the menu bar at the top of the screen is scewered towards the left, So basicaly everything is either on the left side or in the middle.  

I immediately try reconfiguring the xserver with some command i found online.  No good.  I tried uninstalling then reinstalling the ubuntu-desktop.  Still didn't work.  Then I hit the escape button on startup and couldn't help but realize I no longer simply have my generic ubuntu kernal, there's an additional non-generic ubuntu kernel.  

Keep in mind, I have no idea what the above even means.  I'm just mentioning because, keep in mind, I don't even know how to compile an additional kernel.  So either Nvidia's driver did this, or I royally $#%ed up.  And while I'll admit that it would probably be easier for me to just erase everything and reinstall ubuntu (yet again).  I'm kind of hoping there's a way around this.  Maybe just reinstall every package on my cd without formatting the hard-drive?  I'm open to suggestions.  Good ones though, thanks in advance for reading my long *** story.  I'll try and post a pic of my desktop once I find some serverspace.

---

### Post by r4ik on 2007-12-26
Short answer try,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck !

---

### Post by MrTripi on 2007-12-26
that was a nifty program, unfortunately I'm still having the same problem.  I can't help but notice my menu icons aren't pushed over to the left when the resolution is turned way down though.  Is it possible that my monitor drivers are the cause of my probems to begin with?  Whenever I up the resolution to my normal 1200 the top right menu items are pushed over to the left so they're in the center of the menu bar.  However when I'm in 800 they're in the correct position.  Are there any good programs which will set up my monitor drivers for me? :P

---

### Post by MrTripi on 2007-12-26
christ, this is hopeless.  I just freakin hopeless, I use auto-detect and it says I have a plug and play monitor, highest resolution is 640.  I use this driver then I run sudo dpkg-reconfigure xserver-xorg which detects I have a custom monitor and sets it to 1400 for me.  The menu bar is still #%#ed up.  I feel like it's impossible to have a minor problem when you're dealing with this OS.  3formats within the span of 3months is rediculous. Is there seriously no way to just reinstall system files without formatting the entire hard-drive?

---

### Post by daengbo on 2007-12-27
First, for your problems regarding NVidia. The proprietry drivers sometimes cause headaches. There's no way around it. If you use the open source nv driver (sorry, no 3D), you will never have an issue. That doesn't help your Second Life play, though.

Second, you should install Ubuntu with a separate /home parition and leave that unformateed if you DO reinstall. The system files will be restored but all your personall data and preferences will be left alone.

Good luck.

---

