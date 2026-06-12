---
title: "Updated Kernel image via Synaptic, now Linux won't boot"
date: 2005-05-30
forum: Desktop Environments
---

### Post by GTKpower on 2005-05-30
I had a feeling this would happen. I just felt it - I have a very good system-****-up sense . . . . it's like my Grandmother who can feel a tornado coming on, even though it's a beautiful, calm day.

On  Friday, I did an update via Synaptic.  Saw a Kernel-image update and decided to include that as well.  It's an update, after all.

Near then end of doing its thing, Synaptic stops, so I open the console to see what's going on.  Sure enough, I get a yes/no question - something about putting the kernal image on LILO or not (I'm using LILO, not GRUB, since GRUB would never install correctly.)  I chose the most logical thing, and put it with LILO.  Fine.

I reboot Linux for whatever reason, and I get this:

[B]VFS:  cannot open root device "301" or unknown block (3,1)
Please append a correct "root=" boot option
Kernel panic - not syncing : VFS : unable to mount root fs on unknown - block (3,1)[/B]

So, I tried hitting ESCAPE before boot-up to maybe select my previous kernel, but to no avail.

Any help, please?

My console skills are pretty (VERY) basic, so please go easy on me.  ;-)

I'm using WindowsXP to type this thread, and hating every minute of it.  So please, before I slit the back of my knees . . . HELP.

Kind regards,

-Christian.

---

### Post by cutOff on 2005-05-30
Did you see this thread???

[http://ubuntuforums.org/showthread.php?t=36573&highlight=unable+mount](http://ubuntuforums.org/showthread.php?t=36573&highlight=unable+mount)

---

### Post by Robban59 on 2005-05-30
Hi there,

same exact thing happened to me some days ago, updating the Linux images;
now I can't boot Ubuntu anymore !!

Here is my thread describing my problem, hope someone can help me...

[http://ubuntuforums.org/showthread.php?t=38011](http://ubuntuforums.org/showthread.php?t=38011)

Thanks in advance.

---

### Post by GTKpower on 2005-05-30
Not a viable solution in that thread.

The ubuntu dev team NEEDS TO FIX THIS.  

I should be able to run Synaptic, select the available Hoary updates and forget about this.

I'm certainly not going to download another distro just so I can boot into my system.  That's ridiculous, and a "solution" that plays right into the hands of people who think that Linux is nowhere near ready for desktop use.

Ubuntu is supposed to be easy to use.  This kernel issue needs to be fixed.  FYI, although I have all my files backed up, I refuse to go through hell just to boot ino my system.

My hardware is very generic, and has worked with every single Linux distro.

I'm holding Ubuntu responsible for this problem.

---

### Post by Robban59 on 2005-05-31
Hi everybody and especially UBUNTU Dev Team,

there seems to be a problem with the latest kernel image upgrade from Synaptic issued last week, thanks to that I have managed to hose my fine Ubuntu installation, and I'm sure many others have done.

I'm struggling to get it up again, se emy thread a couple of messages above this one, but I'm a newbie so it is not easy.

Please UBUNTU Dev Team fix the offending files, post them in the repositories and issue a nice detailed HOWTO so we can get UBUNTU up and running again, starting from a bootable WIN2K/XP, Hoary Install CD and Hoary LIVE CD or what else; please take into account that reaching the Internet from UBUNTU LIVE or Install might not be possible, only solution for me so far is via W2K to download updated files.

Hope to hear from you soon....

---

### Post by Leif on 2005-05-31
Sorry to hear about your problems. This stuff is unfortunately way beyond my linux skills, but hopefully someone will help you out soon. In the meantime, have you guys reported the bugs at bugzilla ?

---

### Post by GTKpower on 2005-05-31
Seems I'm not the only one.

I apologize if in my previous post I came off as sounding nasty, but the last thing anyone expects is that a simple update would result in a borked Ubuntu installation.  

Hoary, at the very least must be stable enough to allow for a boot, after any kind of update.  It is unacceptable to introduce a buggy kernel update into a stable repository - especially with Ubuntu, since it, more than any other distro out there, strives for excellence.

Anyway, this is just my opinion - hopefully it matters.

I have all my data backed up, and frankly, I simply can't wait any longer for a workable solution.  I use Ubuntu for work, and I need to get it up and running asap.

But won't it be weird when I do the first update through Synaptic, to have to unselect the kernel update?

---

### Post by Robban59 on 2005-06-01
Hi there,

don't ask me why , but I have a strange feeling this might be the solution to our problems :  check in the Ubuntuforums section Official UBUNTU Announcements -> [USN-136-2] Fixed packages for USN-136-1.

I downloaded the three files with WIN2000, now I must find a way to boot with UBUNTU LIVE or Install, get the files probably on a CD and apt-get install them, maybe then LILO will work again, who knows, and we will be able to boot up Hoary again !

I'll be away on holiday and will try it next Monday evening.

Cheers to everybody.

---

### Post by PeteJ on 2005-06-15
Hi all,

Sorry for the long-winded answer, but I think it helps the new folks a little...

=====
Bottom line:  use knoppix to put your root device (mine: /dev/hda2) in the kopt line in your /boot/grub/menu.lst, something like:

# kopt=root=/dev/hda2 ro

(I have a single hard drive "a" and ubuntu is on my second (OK, maybe third) partition "2".  Windows is in my partition "1".  Yours may be different.)

=====

Wow, what a scary morning I've had.  Struggling with getting evolution and gpilotd to sync with my palm vx, I reboot and ... kernel panic.  Now I recall one or more recent auto updates had a kernel something... 

I'm on hoary 5.04 on a thinkpad t21 with pentium III using the 686 kernel.  

My kernel panic error message was something like:

starting ubuntu pivot_root no such file cannot open dev/console

My thinkpad needs a acpi=off in grub menu.lst, so I checked that and that didn't work.  

I googled my error string and found:

[http://ubuntuforums.org/showpost.php?p=42546&postcount=14](http://ubuntuforums.org/showpost.php?p=42546&postcount=14)

But that applied to mac b/w g3.  Regardless, I used my knoppix 3.6 cd to boot to try to implement that solution, but couldn't figure out what to do on my loadmodules set. 

Getting more and more scared and frustrated by the second, I then found Douglas Royds'

[http://lists.ethernal.org/cantlug-0505/msg00783.html](http://lists.ethernal.org/cantlug-0505/msg00783.html)

Using that as a starting point, and luckily I had made a backup of my /boot/grub/menu.lst, while still in knoppix, I did a grep hd of my current and backup menu.lst files.

petjal@gandalf:/boot/grub$ grep hd menu.lst.orig menu.lst
menu.lst.orig:# root            (hd0,0)
menu.lst.orig:# root            (hd0,1)
menu.lst.orig:# kernel  /vmlinuz root=/dev/hda2 ro
menu.lst.orig:## e.g. kopt=root=/dev/hda1 ro
menu.lst.orig:# kopt=root=/dev/hda2 ro
menu.lst.orig:## e.g. groot=(hd0,0)
menu.lst.orig:# groot=(hd0,1)
menu.lst.orig:root              (hd0,1)
menu.lst.orig:kernel            /boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro quiet splash
menu.lst.orig:root              (hd0,1)
menu.lst.orig:kernel            /boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro single
menu.lst.orig:root              (hd0,1)
menu.lst.orig:# on /dev/hda1
menu.lst.orig:root              (hd0,0)

menu.lst:# root         (hd0,0)
menu.lst:# root         (hd0,1)
menu.lst:# kernel       /vmlinuz root=/dev/hda2 ro
menu.lst:## e.g. kopt=root=/dev/hda1 ro
menu.lst:# kopt=root=/dev/hda2 ro acpi=off
menu.lst:## e.g. groot=(hd0,0)
menu.lst:# groot=(hd0,1)
menu.lst:root           (hd0,1)
menu.lst:kernel         /boot/vmlinuz-2.6.10-5-686 root=/dev/hda2 ro acpi=off quiet splash
menu.lst:root           (hd0,1)
menu.lst:kernel         /boot/vmlinuz-2.6.10-5-686 root=/dev/hda2 ro acpi=off single
menu.lst:root           (hd0,1)
menu.lst:kernel         /boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro acpi=off quiet splash
menu.lst:root           (hd0,1)
menu.lst:kernel         /boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro acpi=off single
menu.lst:root           (hd0,1)
menu.lst:# on /dev/hda1
menu.lst:root           (hd0,0)
petjal@gandalf:/boot/grub$

and noticed that the only real difference was that

# kopt=root=/dev/hda2 ro

was missing from the new one (after the kernel update).  (The string appears in the printout above because I did that grep after the fix I'm describing here and I was too lazy to try to recreate it for you all here.)

I tried to make an edit, but knoppix wouldn't let me because hda2 was mounted read only (ro).  So, in knoppix, I closed all windows touching /dev/hda2, checked what was mounted by typing

mount

saw the loopback mount from the above loadmodules fix attempt, and so I did

sudo umount /mnt/initrd

Then from Kristof on [thelist] Knoppix Linux on CD: Write to hard drive safely, I found essentially

sudo mount -o remount,rw /mnt/hda2

sudo vim /mnt/hda2/boot/grub/menu.lst

and added 

root=/dev/hda2 ro

to the beginning of the kopt= line (and put back the comment mark, dummy that I am)
(so it now appears as you see above), like this. 

# kopt=root=/dev/hda2 ro acpi=off

I then ran 

sudo update-grub 

to propogate that change to the boot menu.lst kernels (686, 386, Windows 2000 on hda1/hd0,0).  (I think I did that under knoppix--does that make sense?)

Then rebooted, sighed in relief, and wrote this note.

I hope it helps.

Good luck,
Pete

---

### Post by GBX on 2005-09-02
i have a much easier solution when using lilo
Seems that the Synaptics update didnt run lilo after updating the kernel, so the solution is quite simple. Just set the Linux partition as root directory and run lilo as in the following steps described:

[list=1]
[*]Boot any Live Linux (e.g. Knoppix)
[*]Mount your Linux Partition (e.g. mount /dev/hda1 /mnt)
[*]Type into console: chroot /mnt lilo
[/list]

---

### Post by mortenalver on 2005-09-14
[QUOTE=GBX]i have a much easier solution when using lilo
Seems that the Synaptics update didnt run lilo after updating the kernel, so the solution is quite simple. Just set the Linux partition as root directory and run lilo as in the following steps described:

[list=1]
[*]Boot any Live Linux (e.g. Knoppix)
[*]Mount your Linux Partition (e.g. mount /dev/hda1 /mnt)
[*]Type into console: chroot /mnt lilo
[/list][/QUOTE]

Thanks, GBX, that was the solution for me. I'll be careful with kernel upgrades from now on...

---

