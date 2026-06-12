---
title: "Jaunty video fall down go boom."
date: 2009-04-24
forum: General Help
---

### Post by bishounen on 2009-04-24
So far I have been loving Ubuntu 9.04 on my T60 laptop.

I did an in-place upgrade from 8.10 that went very smoothly about 5 days ago.  It has been working just fine, no problems at all until last night.  I was just sitting on the couch with the laptop surfing and watching T.V.  I shut the laptop down since the battery was getting low, went and grabbed my power adapter, plugged in, booted up and right after the bootsplash  (before X starts)  the video just goes all wonky.  Freaky lines, flashing graphics, no stable picture, just flickering flashing, but mostly black display.

Normally I would assume that this would indicate a hardware failure.  It certainly looked like a fried vid-card or video connector ribbon crack.  So I booted up with my old 8.10 live session disc and it worked fine.  Advanced graphics effects even worked!  So it's NOT a damaged video card or screen.  (whew!  Thank goodness for that!)

Now, I know the 8.10 and 9.04 ATI graphics drivers are different, so I then booted with my 9.04 boot disc I had downloaded and burned for a fresh install on another machine.  It ALSO booted normally AND Extra Effects works great.  So It's not a driver problem.

So now that I know it's not a hardware issue, and not a driver issue, what does that leave me with?  Is it an xorg.conf problem?  If so, why does the video go crazy before the X11 session has started?  I can't even get to the login screen.  Immediately after the bootsplash I lose video capability.  I DO have access to the hard drive via the live boot disc, so I can get data off of there if need be, but I can't boot into the OS to test anything.

Any suggestions?

---

### Post by bishounen on 2009-04-24
Just an update:

I have just tried booting into recovery mode and running both xfix and fsck, no change.

If no one else has any suggestions I may resort to a full wipe and reinstall.  But I'd hate to HAVE to do that over just an error.

---

### Post by El Zoido on 2009-04-24
You did shutdown your Laptop properly, right?

---

### Post by bishounen on 2009-04-24
> **El Zoido said:**
> You did shutdown your Laptop properly, right?


The first time (while it was still working normally) yes.  After that I've had to hold down the power button as nothing else works.  (crtl-alt-delete isn't causing a reboot, for example.)

---

### Post by El Zoido on 2009-04-24
If you can access your harddrive, maybe you could try to overwrite your xorg.conf with a backup.
If you have one.

---

### Post by bishounen on 2009-04-24
Actually, I do have a backup, since the upgrade process automatically creates one.  I'll try using that one and let you know the results.

---

### Post by bishounen on 2009-04-24
Nope, didn't work.  :(

I am loathing having to wipe and reinstall, not because I don't have a data backup, I do.  but because I'll have to spend time re-customizing some of the system.  (Most importantly to eliminate that annoying loud "beep" every time Ubuntu shuts down since version 8.10.)

---

### Post by jamessnell on 2009-04-24
Hmm, that's a pretty weird sounding issue. Are you absolutely certain it's not a hardware issue? Can you get gdm to function properly off a LiveCD?

If you can, then it's got to be either config or drivers... Have you tried using a ghetto video driver, such as "vesa"?

---

### Post by bishounen on 2009-04-24
> **jamessnell said:**
> Hmm, that's a pretty weird sounding issue. Are you absolutely certain it's not a hardware issue? Can you get gdm to function properly off a LiveCD?

If you can, then it's got to be either config or drivers... Have you tried using a ghetto video driver, such as "vesa"?

Works just fine in 8.10 live CD and 9.04 live CD.  Extra desktop effects and everything.  So not a video card problem  (you can't enable extra desktop effects if your vid card is toast and the CPU is running the show.)

I did try replacing the vid driver listed in xorg.conf.  It was listed as "ati"  and I changed it to "vesa".  Didn't make a difference.

I also tried replacing the entirety of xorg.conf with a backup from the upgrades.  Still no change.

At the moment I'm booted into the 9.04 live CD and am about 1/2 step away from just formatting and reinstalling the OS.  But having to reinstall VMWare workstation, and reconfigure all the little customizations such as turning off the system beep and adding in all the little extras I like to have is staying my hand on the wipe in the slim hope that I can avoid it.

Although frankly that's looking less and less likely with each passing moment.  If anyone can offer a good suggestion I will gladly try it.

---

### Post by bishounen on 2009-04-24
Bah.  Forget it.  I'm just going to wipe and reinstall and go from there.  I've got everything critical backed up anyway, so no chance to lose anything important.  I'll update and let you know if that fixed it.

---

### Post by bishounen on 2009-04-24
Yep, that fixed it!

The only thing I can think is that some random driver or critical system file got corrupted during the upgrade process and was causing the entire system to just hang after the bootsplash.

Freaky, but then upgrades can go badly.  This system had already been upgraded from 7.10 to 8.04 then 8.10 and finally 9.04.  I guess it couldn't take it anymore.  Still, 3 solid upgrades is nothing to sneeze at.  Too bad it finally collapsed on the 4th upgrade, but I GUARANTEE it wouldn't have gone as well had I done a Windows upgrade!

Thanks everybody.

---

### Post by jamessnell on 2009-04-24
> **bishounen said:**
> Bah.  Forget it.  I'm just going to wipe and reinstall and go from there.  I've got everything critical backed up anyway, so no chance to lose anything important.  I'll update and let you know if that fixed it.

Please do!

---

### Post by Wiebelhaus on 2009-04-24
> **bishounen said:**
> The first time (while it was still working normally) yes.  After that I've had to hold down the power button as nothing else works.  (crtl-alt-delete isn't causing a reboot, for example.)

I'm sure you just miss-typed but it's "crtl+alt+backspace" not crtl-alt-delete , To restart xserver that is.

---

### Post by bishounen on 2009-04-24
> **jamessnell said:**
> Please do!

It worked!

Just doing a file merge to my home folder from my backup drive now, everything seems to be functioning normally.

---

### Post by bishounen on 2009-04-24
> **sx66gns said:**
> I'm sure you just miss-typed but it's "crtl+alt+backspace" not crtl-alt-delete , To restart xserver that is.

Ah, yeah.  that was a mis-type.  I work in the Win world, so I've gotten used to typing that.  But yes, ctrl-alt-bkspce failed to reboot the system.

Sorry for any confusion.

---

### Post by Wiebelhaus on 2009-04-24
> **bishounen said:**
> Ah, yeah.  that was a mis-type.  I work in the Win world, so I've gotten used to typing that.  But yes, ctrl-alt-bkspce failed to reboot the system.

Sorry for any confusion.

Cool , cool I understand , I work in a world with Windows and gates to.

---

### Post by HPD2 on 2009-04-24
I had the same problem on my dell D810; I thought it might be a heat issue till I talked to a friend who suggested it could be drivers. [My post]("http://ubuntuforums.org/showthread.php?t=1116449"). Does your lapotp happen to have an ATI graphics card?

---

