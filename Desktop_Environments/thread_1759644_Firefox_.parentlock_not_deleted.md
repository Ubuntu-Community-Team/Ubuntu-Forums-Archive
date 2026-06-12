---
title: "Firefox .parentlock not deleted"
date: 2011-05-16
forum: Desktop Environments
---

### Post by RMOP on 2011-05-16
Not reliably, that is. Regularly, I go to start FF only to get the error message that FF is already running (it isn't). The fix ALWAYS entails opening Nautilus and deleting the .parentlock file, which is the file which locks the FF profile. Yes, FF is closed properly each time.

CAVEAT: This problem appears to have emerged only after I moved my FF profile to an NTFS drive so that I could use the same profile from either Windows or Ubuntu. (that much is working nicely, at least!) Further use may prove otherwise, but running FF from Windows does not leave the Windows equivalent (parent.lock) undeleted after an orderly shutdown of FF.

Any suggestions?

---

### Post by chops228 on 2011-06-07
I am having the same problem. Like you, I have Firefox in both Windows 7 and Ubuntu 11.04 pointed to the same profile folder in a NTFS formatted drive.

However, I only have this problem after a reboot. I can close firefox, and then reopen it with no problems. But if I close firefox and then restart my computer, when I try to start firefox I get the "Firefox is already running...." error. I just delete the .parentlock file and it works fine, but it is a bit annoying.

---

### Post by RMOP on 2011-07-31
> **chops228 said:**
> I am having the same problem. Like you, I have Firefox in both Windows 7 and Ubuntu 11.04 pointed to the same profile folder in a NTFS formatted drive...

Well, it's not annoying enough people, based on the replies to this thread. Can't be that we're the only Ubuntu users using a shared profile, and hardly the only ones doing so with the .parentlock issue. It is REALLY annoying.

Surely SOMEONE has SOLVED this problems somewhere along the way.

SOMEONE?

---

### Post by Winelord on 2011-07-31
Is this [link]("http://kb.mozillazine.org/Profile_in_use") any use?
It shows you how to either permanently delete parentlock, or, how to reconfigure your profile. Looks to me like there's a bug in FF that causes you to get that error message because it can't find your profile folder.

---

### Post by RMOP on 2011-08-02
> **Winelord said:**
> Is this [link]("http://kb.mozillazine.org/Profile_in_use") any use?...

Thanks. I'd seen this but hadn't read it as carefully as I did this time. There's definitely some stuff at the end about re-creating the profile that's worth a go. Unfortunately, my Ubuntu SD Card installation decided to auto-trash and nothing I've been able to do has restored it. Hence, I'm stuck w W7 only and can't test the fix. But, the problem was always under Ubuntu and never Windows. When I get a new Ubuntu install on my SD card, I'll see if things clear up, or if the suggestions in the link help.

Back later.

Cheers

---

### Post by RMOP on 2011-09-24
Well, I'm out of ideas. FF has no problem FINDING my shared profile, only in gracefully exiting and removing the .parentlock file. I suppose I could learn how to write a script to run on startup and shutdown just to make sure that .parentlock is removed. I don't like getting down in the weeds like that, but I don't know what else to do.

---

### Post by RMOP on 2011-10-10
It's actually a good idea to talk to one's self if no one is listening, and if the conversation itself makes sense. I think the former condition is largely satisfied (winelord and chops228 excepted), and I'll try to ensure the latter.

This .parentlock business is more complicated than merely deleting the file after exiting FF. If I delete the file from Nautilus, shutdown, reboot and try to open FF, FF behaves exactly as if .parentlock were NOT deleted. If I then open Nautilus, view the files in my FF Profile (and confirm, BTW, that .parentlock is NOT present), I can then open FF w/o any complaints.

It appears that "touching" the FF Profile directory by "merely" viewing it is effecting some action which allows FF to open. What action, I've no clue. But I've replicated this consistently many, many times.

I'd like both an understanding of the problem and a solution. Any solution at this level seem likely to be a work-around, as I'm convinced that there's a bug somewhere. I suppose I might eventually dust off my script-writing skills (never very good under Linux) and see if checking for .parentlock, deleting it if present, and in any event using the ls command to read the directory. This might effect the same result as I'm getting w Nautilus. And, I'll try it manually w/o resorting to a script to see if that does the trick.

If anyone wants to join my private conversation, please jump in!

---

### Post by RMOP on 2011-10-10
Well, silly me. But at least I get to point it out this way.

MOUNT the NTFS Partition on which the FF Profile is stored BEFORE opening FF. Duh. All of this chasing down an undeleted .parentlock file was a red herring. I don't automount my NTFS data drive when Ubuntu starts, hence, it's not available to FF until after I mount it, which of course I had to do when chasing down the .parentlock file.

I've now tried opening FF BEFORE and AFTER simply mounting my NTFS drive via Nautilus (and w/o actually opening the FF Profile folder). FF opens w/o complaint when the partition is mounted, and whines that FF is already running (i.e., can't FIND the FF Profile) otherwise. Simple as that. Solved.

I'll look into mounting my NTFS drive on startup...

---

### Post by RMOP on 2011-10-10
I really did NOT intend to start a blog on this...but, this problem is getting increasingly curious.

If I auto-mount my NTFS data partition, which is home to the FF Profile shared between Ubuntu and Windows, then FF can't open at all, but gives the error when it can't find or open its profile! Presumably something in the /etc/stab caused the directory to be inaccessible to FF, though I've no clue as to why. I can read it from Nautilus after auto-mounting, and can see that there's no .parentlock present. Time to start a new thread to chase that down.

---

### Post by Zeta-K on 2011-10-10
Can you post the contents of your fstab file?

---

### Post by RMOP on 2011-10-10
> **Zeta-K said:**
> Can you post the contents of your fstab file?

Thanks. Did so in a new thread:

[http://ubuntuforums.org/showthread.php?t=1857503](http://ubuntuforums.org/showthread.php?t=1857503)

Request you reply to that thread, as it may get a bit more exposure. Thanks. But, here's the entire fstab:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

#Entry for /dev/sda7 :
UUID=3aa8a07d-d2d5-4779-8a8e-7f17ff37783e	/	ext4	defaults	0	1
#Entry for /dev/sda5 :
UUID=A04A69F04A69C41E	/media/NTFS_Data	ntfs-3g	defaults,user=MyUserID,locale=en_US.UTF-8	0	0
#Entry for /dev/sda6 :
UUID=d6d254c0-fc97-4a07-b03e-8d4d114505a9	/swap	swap	sw	0	0

---

### Post by RMOP on 2011-11-07
I'm marking this solved. The thread referenced above contains the actual solution.

---

