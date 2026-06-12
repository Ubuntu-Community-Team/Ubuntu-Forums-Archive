---
title: "Making a system restore CD from my computer"
date: 2006-02-28
forum: Desktop Environments
---

### Post by jabster on 2006-02-28
Hi.

Is there an easy way to take my current setup on my computer, and basically make a system restore cd/dvd?

Ideally, it'd have all my data and everything, but just getting the system back would be perfectly ok. (I only have a 40G HD.)

I'd like 2 versions:
1. Just put the CD in, reboot, and walk away, as everything is restored to the way it was before I hosed my system (from an errant KDE 4 upgrade for instance). :-)
2. Restore, with some prompting for partitions, etc.

I realize option 2 is much more involved, so I'm really only looking for option 1 at the moment.

I'm running the latest Kubuntu with all the updates.

Thanks,
john

---

### Post by stuporglue on 2006-02-28
> Ideally, it'd have all my data and everything, but just getting the system back would be perfectly ok. (I only have a 40G HD.)

I'd like 2 versions:
1. Just put the CD in, reboot, and walk away, as everything is restored to the way it was before I hosed my system (from an errant KDE 4 upgrade for instance).
2. Restore, with some prompting for partitions, etc.

Well no, because you can't fit all 40 Gb of your disk on a DVD. But you knew that. :-) 

Do you have an external (USB or Firewire) disk? If you do, you could image your drive onto it, then restore it with a pretty simple procedure. (boot to a liveCD, use dd to create the image, or to restore it later).

You could create a tarball of your home directory I guess, and if a) it's smaller than the size of the DVD, and b) you have room to create that tarball, you could tar up your home directory and throw that on a dvd. 

tar czf /tmp/home_backup.tgz /home/$MYUSERNAME

Then burn /tmp/home_backup.tgz to disk

---

### Post by jabster on 2006-03-02
SO basically this then?:
Load up PCLOS, run "dd if=??? of=/temp/??", then when restoring,
"dd if=/cdrom/dir/ of=/dev/hda1"?

Not really sure what to put for the initial "if".

Regarding the 40G on a CD, well, how do all those liveCDs put so much stuff on a single CD? Eh, Mr. Smarty Pants? :-)

thanks for the reply,
john

---

### Post by Alfred_McGee on 2007-12-21
It's a bit surprising there aren't more or better postings on this topic. Windows allows you to simply make a system restore DVD at any point that you decide to quit while you're ahead, so it's odd that  doing the same thing with the otherwise vastly superior Linux operating system is so complicated. Completing a Feisty 7.04 reinstall with all the necessary tweekings always takes me a few weeks, though that's partly because of spotty internet access, plus the fact that I'm still trying out a lot of new applications. I've taken to typing up a little journal of packages and dependencies to be added that aren't regular updates. Apparently a similar log is kept automatically somewhere on my computer, but I'm too much of a newbie to remember where. Writing it yourself definitely helps you get a sense of things, and makes the whole process a lot faster the second time around, especially if you compile from source instead of just apt-getting everything, and also if you keep old tarballs lying around so that you can install without having to download them again. Of course, when I say "system restore DVD," I just mean one for restoring the installed programs, not the various documents and videos you might have collected. Those, if you care about them, should be stored elsewere anyway...

---

### Post by smartboyathome on 2007-12-21
There IS an option for this. Just use [Remastersys 2]("http://www.remastersys.klikit.org/").

---

