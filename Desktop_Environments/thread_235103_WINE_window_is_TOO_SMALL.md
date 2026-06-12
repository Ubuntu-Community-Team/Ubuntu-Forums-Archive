---
title: "WINE window is TOO SMALL"
date: 2006-08-12
forum: Desktop Environments
---

### Post by lonelypauly on 2006-08-12
ive been able to run a few apps with WINE just fine, but the window size is way too small...check it out:

[IMG]http://i6.photobucket.com/albums/y215/lonelypauly/winedesk.jpg[/IMG]

I opened the WINE confg settings, changed them...but the settings keep reverting back to default.  I just tried to open the wine cnfg again with the console and got "module not found"...must be user error, i didn't change anything in the past few hours...hmm?

---

### Post by the-linux-guy on 2006-08-12
Use winetools ([http://www.von-thadden.de/Joachim/WineTools/index.html#download](http://www.von-thadden.de/Joachim/WineTools/index.html#download)) to configure your wine-setup...

---

### Post by lonelypauly on 2006-08-12
Thanks, but im still lost.  there is no support listed for ubuntu on that page...it seems that if its not in the repos then it doesn't work so well.

---

### Post by TheEmb3rEgg on 2006-08-12
Go into the graphics tab in winecfg and enable/change the size of your virtual desktop

---

### Post by lonelypauly on 2006-08-12
Ok, I did that and it is still the same size...640 x 480...i read about wine tools (the wine config gui) but its not in the repositories...hmmm...what should i do? i uninstalled wine and reinstalled...same problem.

---

### Post by kealan on 2008-02-17
I'm having the same problem, it's really frustrating.  What's happening is that when  you run winecfg, there isn't enough room on the screen to reach the apply button, so changes do not go into effect.

---

### Post by kealan on 2008-03-31
Really?  No one can help us?  I've spent many hours on this problem, it's not quite worth reinstalling ubuntu, but it's really driving me nuts.

---

### Post by mcduck on 2008-04-01
> **kealan said:**
> I'm having the same problem, it's really frustrating.  What's happening is that when  you run winecfg, there isn't enough room on the screen to reach the apply button, so changes do not go into effect.

IF you hold down the Alt-key you can move the window from any part of the window. That should allow you to access the apply-button.

Also, do you really need the windows desktop? Wine can also simply run the windows programs as they are, without putting them inside the wine desktop window..

---

### Post by ben2talk on 2008-04-08
Yes, you may need the desktop to be a nice window for sticking to all desktops (such as using NetMeter) and resize the Virtual Desktop to a lovely tiny size.

To get out of this, you can go to the folder 

/home/<*username*>/.wine/

In here are the 'system.reg' 'user.reg' 'userdef.reg'

Here you will find the config files. Personally, I simply 'REMOVED  the 'user.reg' file by renaming it (select, press F2, and change to 00.user.reg. Now your virtual desktop is gone, and you can just open the apps in the normal WINE window (but can't stick it to all workspaces...).

Question: Is there any way to run separate applications with separate settings? i.e. run Netmeter in it's own small desktop 192x162 pixels, but run the Winecfg outside the desktop? separate instance?

(Note: I simply find this a good way to help me find files I need to restore later if I navigate there using a root Nautilus window.... I save the path to a text file on the desktop, for cutting and pasting. Then list inside the window - the two zero's are at the top of the list. It's nicer than adding .BAK, you could do both if you like.)

---

### Post by kealan on 2008-04-14
> **ben2talk said:**
>  I simply 'REMOVED  the 'user.reg' file by renaming it (select, press F2, and change to 00.user.reg. Now your virtual desktop is gone, and you can just open the apps in the normal WINE window (but can't stick it to all workspaces...).

Finally, this worked perfectly, thank you so much for your help!

---

