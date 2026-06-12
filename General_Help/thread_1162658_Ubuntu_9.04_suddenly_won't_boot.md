---
title: "Ubuntu 9.04 suddenly won't boot"
date: 2009-05-17
forum: General Help
---

### Post by TitanTiger on 2009-05-17
I've been using 9.04 on a fresh install for a little over a week now and really enjoying it.  Tonight though, I had to restart and boot into Windows to help my dad with something over the phone.  When I got done, I rebooted and selected Ubuntu.  After the initial Ubuntu logo screen, the screen goes black but never boots up.  It sort of goes completely black, the lights up but is blank.  I tried booting in recovery mode but nothing odd came up.

Have I lost the thing altogether or can I recover my install?

---

### Post by TitanTiger on 2009-05-17
bump.

I really need some help.

---

### Post by TitanTiger on 2009-05-18
bump

---

### Post by TitanTiger on 2009-05-18
I was thinking of installing using Wubi and then see if I can at least recover the files in my old native Ubuntu partition.  Anyone know if that will work?  If I boot into the Wubi install will I be able to mount the old Ubuntu partition?

And will doing this screw up anything?

---

### Post by helofromseattle on 2009-05-18
try checking your filesystem in ubuntu recovery mode or boot into the live cd to try rescuing your system from there or even maybe, backup your data using the live cd then, do a fresh install. Hope this helps.;)

---

### Post by TitanTiger on 2009-05-18
> **helofromseattle said:**
> try checking your filesystem in ubuntu recovery mode or boot into the live cd to try rescuing your system from there or even maybe, backup your data using the live cd then, do a fresh install. Hope this helps.;)

Thanks so much for the reply.

Now, I tried booting into recovery mode but the thing goes so fast I can't hardly read anything.  What exactly do I need to do in recovery mode to check the filesystem?

---

### Post by Legace on 2009-05-18
Did you do anything on Ubuntu prior to the boot failure?

Like installing a driver, a program, etc?

---

### Post by TitanTiger on 2009-05-18
> **Legace said:**
> Did you do anything on Ubuntu prior to the boot failure?

Like installing a driver, a program, etc?

Nope.  When my dad called, I was on a message board in the middle of composing a message.  When I realized I was going to have to get into Windows to help him, I copied and pasted my post into an OpenOffice document, saved it, closed OO, shut down Firefox and then used the menu at the top right to restart the computer.  When the GRUB menu came up, I selected Windows.  

While in Windows I used a screensharing program called Yuuguu to help him and when I was done I shut that down and restarted again intending to go back to Ubuntu and all this started.

---

### Post by TitanTiger on 2009-05-18
> **TitanTiger said:**
> Thanks so much for the reply.

Now, I tried booting into recovery mode but the thing goes so fast I can't hardly read anything.  What exactly do I need to do in recovery mode to check the filesystem?

Ok, I'm in using the live CD and was able to mount the Ubuntu partition.  What do I do from here to backup all my important data?  I'd especially like to back up my network and wireless configurations because both were a b**** to get working the first time.

---

### Post by Legace on 2009-05-18
> **TitanTiger said:**
> Ok, I'm in using the live CD and was able to mount the Ubuntu partition.  What do I do from here to backup all my important data?  I'd especially like to back up my network and wireless configurations because both were a b**** to get working the first time.
I think these for network/wireless:
- /etc/network/interfaces
- /etc/resolv.conf
- /bin/hostname

---

### Post by TitanTiger on 2009-05-18
> **Legace said:**
> I think these for network/wireless:
- /etc/network/interfaces
- /etc/resolv.conf
- /bin/hostname

So if I do a fresh install, I should be able to go in and just drop those files back in there and my wireless and wired network stuff will work again?  Because it was a pain getting them to work.  Neither did initially but I installed wicd and finally got the ethernet interface working.  Then I went through this long process installing fwcutter to get the wireless card at least turning on.  But it wouldn't work in wicd no matter what I tried so I reinstalled network-manager (whatever the original network package is) and everything started working.  I'd really rather not deal with that again.

---

### Post by Legace on 2009-05-18
> **TitanTiger said:**
> So if I do a fresh install, I should be able to go in and just drop those files back in there and my wireless and wired network stuff will work again?  Because it was a pain getting them to work.  Neither did initially but I installed wicd and finally got the ethernet interface working.  Then I went through this long process installing fwcutter to get the wireless card at least turning on.  But it wouldn't work in wicd no matter what I tried so I reinstalled network-manager (whatever the original network package is) and everything started working.  I'd really rather not deal with that again.

I don't think so. I don't know what files you've edited..

Guess you'll have to do it all over again.. Good luck :P

---

### Post by which ones pink on 2009-05-18
Try going into grub, and select Ubuntu and press "e".  Do the same with the first option that pops up.  You'll see a line that's something like "ro quiet splash", change the "splash" to "nosplash" and press "b".  This worked for me when I had the same problem in Intrepid.  If that works, you can edit the grub file and you'll be able to boot normally, except you won't have a splash screen.

Edit: the file is /boot/grub/menu.lst.

---

### Post by TitanTiger on 2009-05-18
> **which ones pink said:**
> Try going into grub, and select Ubuntu and press "e".  Do the same with the first option that pops up.  You'll see a line that's something like "ro quiet splash", change the "splash" to "nosplash" and press "b".  This worked for me when I had the same problem in Intrepid.  If that works, you can edit the grub file and you'll be able to boot normally, except you won't have a splash screen.

Edit: the file is /boot/grub/menu.lst.

Hmm.  Doesn't seem to work.  Just didn't give me the splash screen then boots to a blank screen.

---

### Post by TitanTiger on 2009-05-18
One thing I saw when I tried it again was during the booting up there was one line in all that text that said "acer-wmi - no or unsupported WMI interface - unable to load."

What's that about?

---

### Post by philcamlin on 2009-05-18
boot into live cd and click repair broken system :)

---

### Post by TitanTiger on 2009-05-18
> **philcamlin said:**
> boot into live cd and click repair broken system :)

Where is that option?

---

### Post by TitanTiger on 2009-05-18
BTW, the 9.04 live cd doesn't have the "repair broken system" option.

---

### Post by TitanTiger on 2009-05-18
bump.

Since the 9.04 live CD doesn't have the repair broken system option, how would I run a command that does the same thing to that install after the live CD has booted up?

---

