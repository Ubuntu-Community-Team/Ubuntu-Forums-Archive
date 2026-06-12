---
title: "SOLUTION: Alert! /dev/disk/by-uuid/ ...&lt;your UUID&gt;.... does not exist"
date: 2009-04-16
forum: General Help
---

### Post by Neobuntu on 2009-04-16
FINALLY FIXED THIS ONE!!!!!!! (Can you feel the emotion?)

I was dropped to a shell and stuck in Busy box. None of the suggested commands (or added delays) worked! It' kinda hard to upgrade when you can't boot.

I didn't have a old kernel to select (GRUB) because I just installed clean. It booted but not after an upgrade.

SOLUTION: (From Busybox shell hell.)

From my other saved partition with Hardy 8.04 and using "chroot" (you could use a live CD instead), this is how I fixed my Jaunty 9.04 fresh, beta install; where I could finally boot past (Dropped to shell) busybox again. I looked everywhere and tried everything. NONE of the buzybox suggested commands worked for me. I do NOT have RAID! Their was no UUID or /dev naming error. Only, the following worked for me.

I still do not know why the newly installed kernel failed to boot after upgrading it. Perhaps it didn't upgrade correctly or something because once I got back in, using chroot, I had to run the apt-get fix command that it recommends. Unless that was a limit of the chroot, I don't know. This problem was ugly and I almost gave up.

In a terminal (we're using sudo for root here)
REPLACE "X" with your correct drive number, like /dev/sda2 for example

> sudo mount /dev/sdaX /mnt

(You can cut and paste the commands below)

> sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt /bin/bash

Then:

apt-get .......................
.........................etc.

Install a different kernel if you please.

I believe I did a:

apt-get update
(then the suggested fix command and...)

apt-get upgrade

While the kernel didn't appear to be different, I'm not sure that it wasn't a newer fix of it. It booted! Now, after doing upgrades back in Jaunty again, I'm about to reboot and try the newest kernel (it just installed).

**ADDENDUM:** Good to go!

I hope this helps you as much as it did me!

---

### Post by cowgoeswoof on 2009-04-19
i suffer from this problem aswell.
Where do I find out my dev/sdaX number?

---

### Post by Neobuntu on 2009-04-20
I suggest killing two birds with one stone.

Download and burn a boot CD of something like the Gparted CD. Simply booting this will show you (in GUI) how your partitions are set up.

Plus, you can re-size an existing partition with it, and simply leave a blank space (no need to format it) so that any OS installer can then handle everything else for you.

---

### Post by PlaidRadish on 2009-04-27
I upgraded tonight, and experienced this same error with all the same details/problems in my error message.  I double-checked fstab and menu.lst and the UUID's were all correct, so I began experimenting with my server:

and found: a Secondary (simpler) possible solution to the

[INDENT]"Alert! /dev/disk/by-uuid/ ...<your UUID>.... does not exit"[/INDENT]

error -

Out of morbid curiosity, and after receiving this error (and attempting DOZENS of so-called "fixes"), I decided to boot back into an older kernel through the GRUB menu (an obvious perk over a fresh install).  (You could also attempt this simple solution using a liveCD and mounting your /root partition from a Live Desktop environment)

[INDENT]1) Open a terminal [/INDENT]
[INDENT]2) Type "sudo apt-get dist-upgrade"[/INDENT]
[INDENT]3) When Ubuntu completes all remaining upgrades, reboot.[/INDENT]

For some reason, for Ubuntu-Server Jaunty 9.04 release, there is an upgrade bug.  If you simply run "upgrade" all of the necessary changes do not complete.  A simple "dist-upgrade" completes the circle and flushes out the inconsistencies in drive UUID's.

Good luck!

---

### Post by thrasher6900 on 2009-04-29
I have the same problem, however, for some reason, the driver for my wireless isn't automatically turned on when running live as in the past.

Is there a way to update this from the disk without internet?

I don't understand why the drivers aren't turned on for my wirless card, they are there, i just click activate and then it prompts a reboot, which as you know, doesn't save on a live disk.

Thanks ahead of time.

---

### Post by leonbravo on 2009-05-06
Ducking upgrade, 

I am trying your solution. I started using and older kernel with console mode active (graphical session doesn't work)

But all packages are tried to be dowloaded and the network scripts apparently are not working. It just can't download anything. 

Suggestions are wellcome.  


> **PlaidRadish said:**
> I upgraded tonight, and experienced this same error with all the same details/problems in my error message.  I double-checked fstab and menu.lst and the UUID's were all correct, so I began experimenting with my server:

and found: a Secondary (simpler) possible solution to the

[INDENT]"Alert! /dev/disk/by-uuid/ ...<your UUID>.... does not exit"[/INDENT]

error -

Out of morbid curiosity, and after receiving this error (and attempting DOZENS of so-called "fixes"), I decided to boot back into an older kernel through the GRUB menu (an obvious perk over a fresh install).  (You could also attempt this simple solution using a liveCD and mounting your /root partition from a Live Desktop environment)

[INDENT]1) Open a terminal [/INDENT]
[INDENT]2) Type "sudo apt-get dist-upgrade"[/INDENT]
[INDENT]3) When Ubuntu completes all remaining upgrades, reboot.[/INDENT]

For some reason, for Ubuntu-Server Jaunty 9.04 release, there is an upgrade bug.  If you simply run "upgrade" all of the necessary changes do not complete.  A simple "dist-upgrade" completes the circle and flushes out the inconsistencies in drive UUID's.

Good luck!

---

### Post by leonbravo on 2009-05-06
> **leonbravo said:**
> Ducking upgrade, 

I am trying your solution. I started using and older kernel with console mode active (graphical session doesn't work)

But all packages are tried to be dowloaded and the network scripts apparently are not working. It just can't download anything. 

Suggestions are wellcome.


A simple solution would be run the upgrade from console. I have a alternate cd but I don't know how to run the upgrade without using graphical interface and without an internet, I think that is the purpose of the Alternate CD at first place.

---

### Post by Neobuntu on 2009-05-07
OK look. I did a clean install, it worked but not after an upgrade. That's why I had no old kernel to fall back on.

I had spent time tweaking a bunch of stuff the way I wanted it and was actively using it. Else, I would have simply done a new, fast and clean install.

Therefore, I had fun with the change root solution and want to make it better known. So, if and only if somebody got into a similar situation, they could get out easy.

If all else fails, it's fairly fast and easy to back up your stuff (you can't live without) and just do a new clean install. These rare upgrade failures, pass quickly, and so shouldn't reoccur on you.

So, this all makes a case for a more (average visa-vie, as much as possible) completely tweaked desktop solution; upon clean install. AKA, a better pre-finished distribution.

Obviously, non-free installation parts are a PITA. So, if it's not already done, like with Mint (distribution), they really should be a one click affair (or easier!). It's getting better. It needs to.

Of course, you will always want something different; than just about anybody else sets, but we can do better work, to keep it to a minimum.

Here's an idea. I know everything is in /home but how about a user friendly app to backup and restore all the APPROPRIATE settings for a new clean install. This, including translation to the next release(differences where needed). Perhaps then incorporated into the install (like the migration help, but for your old 'open' install). Do we deserve any less? :)

All this, is why it needs to be set up for EXTREME ease and on clean install. Even though, super geeks don't need it. It saves us all time and does not hurt the super technical(but save all, the time). Some is done now and more is needed.

Also, perhaps we should promote mainly, the clean install. This would probably stabilize everyone's collective installs better, by in large. The dream of continuous (release or "dist" tier) upgrading (I'm not talking about regular sweet in-release upgrades) is not better than clean installing (with Ubuntu so far). Ubuntu moves(changes core) to fast (and better core changes are good, just not for dist-upgrades).

---

### Post by sk2 on 2009-05-21
Mounting using a LiveCD as per the first post fixed my problem when upgrading to Jaunty.
Thanks for sharing the solution, saved endless Grub configuration mangling in vain.
Cheers!

---

### Post by Neobuntu on 2009-05-28
> **sk2 said:**
> Mounting using a LiveCD as per the first post fixed my problem when upgrading to Jaunty.
Thanks for sharing the solution, saved endless Grub configuration mangling in vain.
Cheers!

Hey, thanks for the feedback and a successful report from the live CD method. 

I sincerely hope this all helps us out; when no older kernel is there to fall back upon.

Oh, and you guys with wireless problems might just bite the bullet and plug in a hardwired (Ethernet) for your Internet access, upon installation. You know, KISS when you can. :)

PS. I'm currently "peaved"-off at Kubuntu 9.04 right now. Yet, I'm still helping. :)

---

### Post by Blempis on 2009-06-17
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/199573](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/199573)

"Solution:
After activating AHCI in the bios setting and booting from CD/DVD one need to press F6 to enter further boot parameter: pci=nomsi
Now the hdd and other sata devices are recognized correctly due the installation. Don't know if its really a bug.."

I tried this solution but couldn't find that pci=nomsi option anywhere. Then I tried alternate installation and Fix broken system optiion. Following alternate cd's instructions I finally found an option to mount sda1 but this led to problems. My root was now /,/sda1. Then I simply replaced another full copy of the original hard instead that weird /,/sda1 -disk and problem was solved.

While this is not an accurate solution I still hope it was helpful.

---

### Post by jdieter on 2009-08-25
Exact same problem. I tried this method, and apt-get said:
0 Upgraded, 0 newly installed, 0 to remove and 0 not upgraded
When I reboot, I get the exact same error. 


> **PlaidRadish said:**
> I upgraded tonight, and experienced this same error with all the same details/problems in my error message.  I double-checked fstab and menu.lst and the UUID's were all correct, so I began experimenting with my server:

and found: a Secondary (simpler) possible solution to the

[INDENT]"Alert! /dev/disk/by-uuid/ ...<your UUID>.... does not exit"[/INDENT]

error -

Out of morbid curiosity, and after receiving this error (and attempting DOZENS of so-called "fixes"), I decided to boot back into an older kernel through the GRUB menu (an obvious perk over a fresh install).  (You could also attempt this simple solution using a liveCD and mounting your /root partition from a Live Desktop environment)

[INDENT]1) Open a terminal [/INDENT]
[INDENT]2) Type "sudo apt-get dist-upgrade"[/INDENT]
[INDENT]3) When Ubuntu completes all remaining upgrades, reboot.[/INDENT]

For some reason, for Ubuntu-Server Jaunty 9.04 release, there is an upgrade bug.  If you simply run "upgrade" all of the necessary changes do not complete.  A simple "dist-upgrade" completes the circle and flushes out the inconsistencies in drive UUID's.

Good luck!

---

### Post by jdieter on 2009-08-25
As I said, the dist-upgrade didn't work. So I edited /etc/fstab and replaced the UUID with /dev/sda1 - that didn't work either.
So I edited menu.lst and all the UUID in it already matched the ones that blkid showed.

No idea where to go from here. 

> **jdieter said:**
> Exact same problem. I tried this method, and apt-get said:
0 Upgraded, 0 newly installed, 0 to remove and 0 not upgraded
When I reboot, I get the exact same error.

---

### Post by AjitJor on 2009-09-07
Had the same issue myself. This happened after I made the regular system update (using the gui) which I apparently did not do for ~2 months (already running 9.04). The fix was by using the tips of the first post here. But apparently I was already up to date. I checked that my fstab uuid is identical to the uuid specified in "root=...." boot sequence. It did. 

What did the trick ? I just edited (remember the first post here, with all the 'mount's lines) /boot/grub/menu.1st and added an entry for the latest kernel image I could find under /boot. (copy-n-paste old menu.1st entry and just change the kernel name - MAKE A COPY OF THE FILE BEFORE EDITING ... using vi or nano)

and that's it. did a reboot and the new kernel just booted fine.

Really sad that it happened in Ubuntu. This should not happen in such a desktop oriented dist which I recommend to almost everybody both at work and home, and mostly for people that are not friends of the command-line.

---

### Post by thesiant on 2009-09-24
I'm having this same problem with my primary system which I have Kubuntu 9.04 installed. You know something? I don't want to fix it! I am trying to find an OS that's about productivity not 100s of hours of learning backend technical stuff. I use my computer to edit my photos and also store them. They are precious to me and so is my music collection. To this day I've never had a Windows machine or Macintosh (which is what I'm using to write this) flake on me this badly. Linux is known for its security and stability? My *** it's stable... And curb yourselves at piping up about how badass and powerful a system it is at the command line level. I am not scared of using shell commands. But, this is absolutely gay. I am an idiot to have recommended this OS to anyone or to have trusted that these guys value my data whatsoever. If they had, there would have been a lot more time put into each dist-upgrade before its release to ensure it would succeed without such massive problems ever being possible. I can hear the admonishing, "anything can happen, you should've done a backup." I have my stuff backed up, on a drive formatted to ext3 - absolutely useless to me now - this OS is in serious need of work. 
I loved Linux, this feels like betrayal by someone you really trusted not to let you down. Had this been the first major screw up in Ubuntu I might've felt different but there's been other enormous bugs too big to really be okay. I'm certainly done recommending it and I'm reverting to Mac or, on PC hardware, the only thing truly viable is virtualization.

---

### Post by jdieter on 2009-09-24
NONE of the "fixes" in this thread work. Machine is toast. Can't BELIEVE this has been going on for months - and no one has fixed it. Is this not posted in the correct place? Actually, there is one fix that worked for me. I bought a mac.

---

### Post by stormfrog on 2009-09-29
> **Neobuntu said:**
> FINALLY FIXED THIS ONE!!!!!!! (Can you feel the emotion?)

I was dropped to a shell and stuck in Busy box. None of the suggested commands (or added delays) worked! It' kinda hard to upgrade when you can't boot.

I didn't have a old kernel to select (GRUB) because I just installed clean. It booted but not after an upgrade.

SOLUTION: (From Busybox shell hell.)

From my other saved partition with Hardy 8.04 and using "chroot" (you could use a live CD instead), this is how I fixed my Jaunty 9.04 fresh, beta install; where I could finally boot past (Dropped to shell) busybox again. I looked everywhere and tried everything. NONE of the buzybox suggested commands worked for me. I do NOT have RAID! Their was no UUID or /dev naming error. Only, the following worked for me.

I still do not know why the newly installed kernel failed to boot after upgrading it. Perhaps it didn't upgrade correctly or something because once I got back in, using chroot, I had to run the apt-get fix command that it recommends. Unless that was a limit of the chroot, I don't know. This problem was ugly and I almost gave up.

In a terminal (we're using sudo for root here)
REPLACE "X" with your correct drive number, like /dev/sda2 for example



(You can cut and paste the commands below)


Then:

apt-get .......................
.........................etc.

Install a different kernel if you please.

I believe I did a:

apt-get update
(then the suggested fix command and...)

apt-get upgrade

While the kernel didn't appear to be different, I'm not sure that it wasn't a newer fix of it. It booted! Now, after doing upgrades back in Jaunty again, I'm about to reboot and try the newest kernel (it just installed).

**ADDENDUM:** Good to go!

I hope this helps you as much as it did me!


I ****** adore you man! Ive been spending the whole evening to sort this out. With your solution I am finally able to boot my Ubuntu system!

Thanks!!!!! Getting my work computer up and running means everything to me since I run a small webdesign company =)

*happy and dances around the appartment*

Now, of course, Gnome wont load since the new graphics drivers are fubar. But thats a whole other issue :)

---

### Post by atoztoa on 2009-11-11
-- Same reply I gave to two more threads here itself :) --

Try changing the mapping in /etc/fstab from UUID to /dev/sda... (you will need to mount the partition separately after booting from Live CD).

I came across lots of problems during my install of Karmic... read it fully and you will get some insight...

[http://www.atoztoa.com/2009/11/booti...-downfall.html](http://www.atoztoa.com/2009/11/booti...-downfall.html)

_ATOzTOA
[www.atoztoa.com](www.atoztoa.com)

---

### Post by Charkel on 2009-12-29
Thank you for this man! Back into Ubuntu now :)
Big love <3

---

### Post by samquixote on 2009-12-31
As many did, I too had this problem, but my solution was different.

System: Dell Mini 9, 1GB Ram, 64GB SSD
Partitions: 8GB root (sda1), 56GB /home (sda2)
Upgrading from 9.04 to 9.10 (2.6.31-16 kernel)
All went well, no issues, until reboot - hang, in all kernel choices!
Could boot 9.10 from USB key (LiveCD).
After much reading about this issue, and exploring my system (via USB boot), I found a process that worked for me without risking kernel 'diddling'.

Solution:
Boot via USB key.
Mount SSD root (e.g. as /mnt), if not automatically done by LiveCD system.  Mine was not mounted, although sda2 was (as /media/<uuid>).  This may be a symptom/clue to whatever the problem was with my system.
Edit /mnt/boot/grub.lst and added a modified duplicate of 1st entry:
   added unique label to 'title' line (so it can be id'ed from the list!)
   changed 'uuid  <uuid>' line to 'root (hd0,0)'
   modified 'kernel' line changed root=UUID=<uuid> ... to root=/dev/sda1 ...

In /mnt/dev/disk/by-uuid there was no entry for the UUID link to sda1 even though in by-name and by-id all expected entries were there.  So I created the missing link
ln -s <uuid> ../../sda1 
Whether this was necessary or not ...

Shutdown.
Boot and select new entry and viola it worked!

I could have left it there and made that entry the default GRUB choice, but I decided to upgrade to GRUB2.  Excellent instructions in wiki.ubuntu.com/Grub2
After that upgrade, reboot, and everything still working.

GRUB2 uses UUIDs, so why that worked and GRUB1 only worked for /dev/sda1, I do not know.  If anyone has any info ...

Also, the link in /dev/disk/by-uuid that I made disappeared after reboot, and does not appear to be subsequently needed.  Do not know why, or if it was needed for reboot after menu.lst modification.  Again if anyone ...

Note: the 9.10 upgrade kept everything as it was in 9.04, including the WiFi connection, contrary to some reports.  The only issue I have now is Bluetooth - the default power on is annoying, but this is for another thread.

Hope this is of help to others.

...sam

---

### Post by new lin on 2010-01-01
[http://ubuntuforums.org/showthread.php?t=1369580](http://ubuntuforums.org/showthread.php?t=1369580)

In above  the link i faced the same problem 

How could i get to terminal to do those commands ?

Using the live cd did not give me the right to execute the command saying that the device or file not found or does not exist

---

### Post by ian_hawdon on 2010-02-18
@Neobuntu

Cheers mate, don't know how this happened in the first place, but your solution did the job perfectly :-)

---

### Post by lerwys on 2010-02-26
Yes!

It worked for me! Thank you very much!

Just to my knowledge: what are those command in the second quote for? (i'm a linux newbie)

Why do I need to remount those directories again in my recently mounted drive (sdaX)?
What does the /etc/resolv.conf stands for?
And the last command. chroot?

If anyone could help me learing those commands I would be very glad! If not, I'll try looking over the internet for more information about them.

Thank you very much in advance!

---

### Post by faheyd on 2010-03-21
> **lerwys said:**
> Yes!

It worked for me! Thank you very much!

Just to my knowledge: what are those command in the second quote for? (i'm a linux newbie)

Why do I need to remount those directories again in my recently mounted drive (sdaX)?
What does the /etc/resolv.conf stands for?
And the last command. chroot?

If anyone could help me learing those commands I would be very glad! If not, I'll try looking over the internet for more information about them.

Thank you very much in advance!


  I wanted to say that doing the dist-upgrade (after the upgrade to 9.10) did not work for me.  I had to use the alternate boot cd, repair system selection, mount my partitions (read your /etc/fstab to figure that out), and then in console ' sudo apt-get remove dmraid ' .
  This removed the raid detection and my system booted. For some reason on my amd system, the ubuntu dmraid package thought I was configured for raid, which I was not. 
  So, use the other posts to figure out how to boot from the alternate cd, how to mount your drive(s), then do the remove package.  
  My system was quite different the way I had it set up, so I won't post the fstab file, it will only confuse people.

---

### Post by eckschi on 2010-06-15
Maybe this will also shed some light... 
[https://bugs.launchpad.net/ubuntu/+source/devmapper/+bug/358654](https://bugs.launchpad.net/ubuntu/+source/devmapper/+bug/358654)

---

### Post by snofink on 2010-12-01
Thanks Neo! This solution guided me in the right direction but I had a slightly different problem.

After running "sudu blkid" and verifying the uuid was correct in /proc/cmdline and the /etc/fstab UUID (once my /dev/sda1 was mounted) were correct, I did a little more searching and found a bug logged against this.

These are the additional steps that fixed the problem for me.
```

sudo dpkg-reconfigure udev

# change version to what is relevant for you
sudo update-initramfs -u -k 2.6.31-14-generic
```

[https://bugs.launchpad.net/ubuntu/+source/devmapper/+bug/358654/comments/17](https://bugs.launchpad.net/ubuntu/+source/devmapper/+bug/358654/comments/17)

---

### Post by dstudio101 on 2011-02-28
Have the same problem.  still testing 1st thread as this is all too alien for now.

---

