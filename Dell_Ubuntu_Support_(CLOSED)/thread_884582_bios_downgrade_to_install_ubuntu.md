---
title: "bios downgrade? to install ubuntu"
date: 2008-08-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by boyofford on 2008-08-09
Hi was running vista and ubuntu studio dual boot on my 530s (dual core 3ghz) unforunetly after a reinstall of both OS i've ended up only being able to boot into vista, 
thing is, i upgraded the bios just prior to upgrade and think this may be preventing ubuntu loading.
can use liveCDs and can install various ubuntu versions but always end up with a unbootable install, just gets past splash but not to login.
can't find anyway round this,
can't seem to downgrade bios using files from dell site, is there a way of doing this?

the bios version its on now is 530_1015
plz ask for any details is you can think of another way round it!

---

### Post by tamoneya on 2008-08-09
even if you manage to find the older bios files to flash im not certain if the bios will allow you to do this.  The bios will see that you are trying to load an old version and complain.  Some bioses will just warn you and some flat out wont downgrade themselves so im not sure about your specific bios.  It is probably better if we work to solve your problems with the current bios.

---

### Post by Kaemon on 2008-08-09
Isn't there an option in the settings (press del or f2 or f8 at start up or something after dell splash screen) to return the bios to factory defults?

---

### Post by tamoneya on 2008-08-09
> **Kaemon said:**
> Isn't there an option in the settings (press del or f2 or f8 at start up or something after dell splash screen) to return the bios to factory defults?

factory defaults does not equal old BIOS.  It is the factory settings for the current BIOS that you have installed.

---

### Post by boyofford on 2008-08-10
> **tamoneya said:**
> even if you manage to find the older bios files to flash im not certain if the bios will allow you to do this.  The bios will see that you are trying to load an old version and complain.  Some bioses will just warn you and some flat out wont downgrade themselves so im not sure about your specific bios.  It is probably better if we work to solve your problems with the current bios.


found the older bios files as you said, but no joy on install, just says there older than current bios. 
think i'll just have to live with vista for a bit till either someone more knowledgeable than me finds a workaround or the next bios upgrade which hopefully might work!

---

### Post by boyofford on 2008-08-11
same problem with wubi installer!! just gets past splash but not to login grrrr!!

is it wrong that i hope someone else gets this problem?! then they can figure it out and tell me what i'm supposed to do!!! Grrrrrr....

---

### Post by prinknash on 2008-08-11
> **boyofford said:**
> same problem with wubi installer!! just gets past splash but not to login grrrr!!

is it wrong that i hope someone else gets this problem?! then they can figure it out and tell me what i'm supposed to do!!! Grrrrrr....

Are you running Ubuntu Hardy? If so, there's a known problem with the Inspiron 530 which could be causing your problem. It can be solved in two ways.

One is to go into the BIOS and change the SATA setting from IDE (the default) to RAID. That should fix it - but the downside for people (like you) who dual-boot is that Windows won't then boot unless you change the setting back again. Which is tedious. (It's fine for me, though, because I only have Ubuntu on my Inspiron 530N - no Windows at all.)

The other way to solve the problem is to use the GRUB boot option all_generic_ide when starting up Ubuntu - preferably by adding it in the appropriate place to the file menu.lst. That way you can boot both Ubuntu and Windows.

Try Googling Inspiron 530 SATA IDE and you'll find references to this issue.

p

---

### Post by boyofford on 2008-08-11
> **prinknash said:**
> Are you running Ubuntu Hardy? If so, there's a known problem with the Inspiron 530 which could be causing your problem. It can be solved in two ways.

One is to go into the BIOS and change the SATA setting from IDE (the default) to RAID. That should fix it - but the downside for people (like you) who dual-boot is that Windows won't then boot unless you change the setting back again. Which is tedious. (It's fine for me, though, because I only have Ubuntu on my Inspiron 530N - no Windows at all.)

The other way to solve the problem is to use the GRUB boot option all_generic_ide when starting up Ubuntu - preferably by adding it in the appropriate place to the file menu.lst. That way you can boot both Ubuntu and Windows.

Try Googling Inspiron 530 SATA IDE and you'll find references to this issue.

p
 tried both methods but nether wotked so went back to gutsy versions and having same problems with them!
figure its got to be something to do with my stupid bios upgrade mistake! 
tried completly wiping hard disk and just installing ubuntu gutsy 32bit (which i've had on this computer before) and eactly same problem!!

---

### Post by boyofford on 2008-08-11
Just realised my dicription isn't very exact!

bacically can use livecd (at last for gutsy, not tried hardy) no problem and no things needed to be added to boot line thingy.

but on install of gutsy 32bit ubuntu, gutsy 64 bit ubuntu studio,  hardy 32bit ubuntu or hardy 64bit ubuntu studio all goes fine untill reboot time!

get to boot options, see splash relevant to version being attempted, seems to load then get to part of boot where you just have a round mouse curser(or a X curser) and thats as far as it gets! can move curser about with mouse, but keyboard does nothing, caps lock light on but thats it! can't ctrl/alt/delete can't ctrl/alt/f1, can't do anything but force computer to switch off by holding in power button!

have tried the workarounds for the sata problem, but don't think thats my problem as i can't even get the gutsy versions working again, and i've never had problems with gutsy on this computer before.

i can get into recovery options, but don't really know what to do when i'm in there, bit of a novice to linux.

---

### Post by prinknash on 2008-08-11
> **boyofford said:**
> tried both methods but nether wotked so went back to gutsy versions and having same problems with them!
figure its got to be something to do with my stupid bios upgrade mistake! 
tried completly wiping hard disk and just installing ubuntu gutsy 32bit (which i've had on this computer before) and eactly same problem!!

Sorry my suggestions didn't help. All I can say is that I'm running an Inspiron 530N with Ubuntu 8.04.1 and have upgraded the BIOS to version 1.0.15 with no problem - so I don't think there's anything intrinsically wrong with running Hardy on that BIOS.

p

---

### Post by boyofford on 2008-08-12
> **prinknash said:**
> Sorry my suggestions didn't help. All I can say is that I'm running an Inspiron 530N with Ubuntu 8.04.1 and have upgraded the BIOS to version 1.0.15 with no problem - so I don't think there's anything intrinsically wrong with running Hardy on that BIOS.

p

cheers for info, if bios version is working on yours than shouldn't be bios problem then, i'll have to have a think!

just a little question, how did you upgrade your bios in ubuntu?
I upgraded mine in windows, couldn't see the ubuntu option, or did you use dos option?

---

### Post by PCessna on 2008-08-12
> **boyofford said:**
> Hi was running vista and ubuntu studio dual boot on my 530s (dual core 3ghz) unforunetly after a reinstall of both OS i've ended up only being able to boot into vista, 
thing is, i upgraded the bios just prior to upgrade and think this may be preventing ubuntu loading.
can use liveCDs and can install various ubuntu versions but always end up with a unbootable install, just gets past splash but not to login.
can't find anyway round this,
can't seem to downgrade bios using files from dell site, is there a way of doing this?

the bios version its on now is 530_1015
plz ask for any details is you can think of another way round it!

You should never down-grade a BIOS, infact, check for UPGRADES,  I'm sorry I can't help you any further then that advice, but please  keep  that in mind.

---

### Post by prinknash on 2008-08-12
> **boyofford said:**
> cheers for info, if bios version is working on yours than shouldn't be bios problem then, i'll have to have a think!

just a little question, how did you upgrade your bios in ubuntu?
I upgraded mine in windows, couldn't see the ubuntu option, or did you use dos option?

There is a Ubuntu method but, as far as I could see, it wasn't available for the Inspiron 530(N). That stopped me for a while, given that I don't have Windows on this particular machine. Eventually I gathered my courage and made a Bart PE CD, so that I could upgrade the BIOS from a Windows environment. Worked fine, and I've now upgraded the BIOS twice with no ill effects.

p

---

