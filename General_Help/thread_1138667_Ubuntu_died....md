---
title: "Ubuntu died..."
date: 2009-04-26
forum: General Help
---

### Post by aeltester on 2009-04-26
Hey guys,

so I was just working on my mint 6 (ubuntu) machine, running amarok and arranging pictures in digiKam while probably some usual threads were open in the background (no downloads, no heavy work) when all of a sudden the music started to get bumpy, the mouse lagged and the hard drive worked like crazy. I'm usin' this machine without change for almost a year now and have never encountered problems. I didn't mess with xorg, menu.lst (grub) or anything else. I thought something bad was happening so I pressed the reset button.
everytime it comes to grub trying to load my mint, my screen goes "no signal" and the computer reboots.
Luckily I've got another system on the hard drive which I loaded into and backed up everything valuable (pictures, music, documents).
What could it be that just died all of a sudden and seemingly can't be revived anymore? which way is there to avoid reinstalling or to at least avoid having to reconfigure everything?

just for testing I went in /etc/default/bootlogd and enabled logging. after a couple boots, /var/log/boot still says that nothing has been logged yet so Ubuntu seems to be quitting before doing anything at all.

Any suggestions appretiated

hf
:P

---

### Post by oldos2er on 2009-04-26
If you can boot into recovery mode, try running fsck.

---

### Post by nandemonai on 2009-04-26
Sounds like corruption or hardware failure to me.

Could be any number of things.

General things to check..

Run a Live CD, does the machine still refuse to boot etc?

As suggested above try fsck in recovery console.

If you're still getting issue even with a live CD then it's time to look at things like overheating, dying power supply, check the capacitors on the motherboard etc etc etc.

Best of luck with it.

---

### Post by aeltester on 2009-04-27
thanks for your replies...

BUT I am using Ubuntu 8.04 on this exact machine. same hard drive, different partition. everything else of course hasn't been touched and works like a charm.
so it's not the hardware's fault for once :(

if recovery mode is changing the line in menu.lst

from "ro quiet splash vga=..." to "ro single", I tried that already and saw nothing but "no signal" and experienced reboots.
I'll do an fsck but I don't expect any broken secs...

thanks though
hf
:P

---

### Post by Grenage0 on 2009-04-27
A working system on another partition does not rule out a drive failure.  They frequently die a bit at a time.

---

### Post by kostkon on 2009-04-27
Maybe one process was just trashing the disk (for some unknown reason) and the reset that you did corrupted your Mint installation.

That's the only sensible explanation I can think of.

---

### Post by aeltester on 2009-04-27
probably... I'm getting to think that something might have shot my partition table and grub now always points into nowhere. that's the only reason i can think of that would stop my beloved linux from telling me about its problems.
Right now I'm fscking an ext3 external hard drive whose fs has been played around with by effing m$ products. I hope I'll then be able to make an external backup before messing up my partition table irreversibly.

thanks for any help already

still open for suggestions

hf
:P

---

### Post by Psychopump on 2009-04-27
If you have the funds, I HIGHLY recommend backing up all your files to a NEW external HDD. After that I would install a NEW HDD into my PC and start fresh.
I have lost too much data to failing HDDs to ever want to see it repeated.

---

### Post by mixmaster on 2009-04-27
> **aeltester said:**
> I thought something bad was happening so I pressed the reset button.

Unhelpful after the event but I have to say this is almost never a good idea.  Even with modern journalling file systems it is possible to corrupt the filesystem doing this.  More importantly, if a HD is on the way out there is a good chance it will not come back after this action.  If you think the hardware is malfunctioning it is probably best to shut down any offending apps and immediately attempt to backup whatever you treasure most.

About the only time a reset is appropriate (apart from a totally hung system) is if you believe a runaway or malicious program is actively damaging your files.

---

### Post by aeltester on 2009-04-27
it was quite totally hung...
so that i wasn't able to shut down anything at all.
and this NEVER EVER happened before (and on a system as fast as mine, there should be no way to get it to die like this) so I had reason to think something was damaging something.
thanks for your advice about backing up immediately. It's so good that I followed it :D

yeah, now that fsck is trying for a couple of hours to repair this effing filesys on the external hdd (500 gig) I'm thinking about killing the whole task, maybe lose data and then format the hdd.
what is not an option is reinstall my system without a way to restore all settings... I'll rather mess with all this for a while.

thanks again guys

hf
:P

---

### Post by mixmaster on 2009-04-28
Just one other suggestion, then.  I've seen machines which appeared to be totally hung when accessed locally but which would still respond to ssh access from another machine.  If your system appears totall fubar'd it is worth attempting to log in remotely if you have another system.  Sometimes you can do backups, force a graceful shutdown or even free up the system that way - it was a frequent lifesaver a few years ago when the screensaver would lock up the system.

---

### Post by aeltester on 2009-04-28
thanks

a short update:
fsck worked more than 24 hours trying to repair the ext3 fs on the external hdd. well, i killed it. linux still wouldn't mount it. But with windows and ext2fs I'm able to access all the files that supposedly got severely damaged.
My problem now is, that windows won't delete anything from that harddrive plus I can't backup anything from a linux distro to it because m$ windows is too effing stupid to read the file names (so I still hate it).
Is there a way to maybe get a decent shell or anything on xp that would be able to do both, read the fs and handle the file names?

again, any help appreciated

hf
:P

EDIT: just found out cygwin was not mounting on its own but able to work with what is mounted by xp even if not directly. so it seems to be doing the job...

EDIT2: I was wrong... cygwin also won't handle the filenames...

---

