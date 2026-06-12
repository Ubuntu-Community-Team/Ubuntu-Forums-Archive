---
title: "Help with Wubi Ubuntu Install!"
date: 2009-01-28
forum: General Help
---

### Post by cbowencc on 2009-01-28
Hey guys, I recently tried to install Ubuntu using the easiest known method to me, Wubi. I ran Wubi, and it downloaded, did it's thing, then said I needed to reboot at some point for the changes to take effect. I clicked reboot now, then rebooted, and chose the Ubuntu option from the dual boot menu. It showed the Ubuntu Logo with a loading bar for about 3-4 minutes, then went into a different all-text terminal-esque screen. It says something like: BusyBox 1.10.2 Ubuntu6 (Blah Blah Blah) Built in Shell (ash) then below that "Enter 'Help' for a list of commands"
then a prompt that said "(initramfs)". It stays at this screen indefinitely, and I have no idea what to do! Please help.
Thanks In Advance, 
Connor

---

### Post by Feivel on 2009-01-28
> **cbowencc said:**
> Hey guys, I recently tried to install Ubuntu using the easiest known method to me, Wubi. I ran Wubi, and it downloaded, did it's thing, then said I needed to reboot at some point for the changes to take effect. I clicked reboot now, then rebooted, and chose the Ubuntu option from the dual boot menu. It showed the Ubuntu Logo with a loading bar for about 3-4 minutes, then went into a different all-text terminal-esque screen. It says something like: BusyBox 1.10.2 Ubuntu6 (Blah Blah Blah) Built in Shell (ash) then below that "Enter 'Help' for a list of commands"
then a prompt that said "(initramfs)". It stays at this screen indefinitely, and I have no idea what to do! Please help.
Thanks In Advance, 
Connor

Reboot, choose Ubuntu, hit ESC and choose verbose. Either it will continue booting all the way or it will at least tell you what point is causing problems.

---

### Post by cbowencc on 2009-01-28
Thanks, I'll try that and report back.

---

### Post by beyboo on 2009-01-28
This is normal for Intrepid Wubi installations. 3 installations so far and I have the same experience. Just reboot, then u will also get some long wait times on swap file inits... i guess thats normal with intrepid. ...

---

### Post by Feivel on 2009-01-28
> **beyboo said:**
> This is normal for Intrepid Wubi installations. 3 installations so far and I have the same experience. Just reboot, then u will also get some long wait times on swap file inits... i guess thats normal with intrepid. ...

For some reason the "delay" is almost non-existent when you choose verbose.

---

### Post by constable24601 on 2009-01-28
I had the same install problem, and followed the advice to hit Esc and select verbose.

The system went through many configuration lines but is now hung much later in the boot process with the Busybox logo again, and the prompt reads

(initramfs)

If the system hang can be identified, the last two lines of the scrolling boot screen read:

Clocksource tsc unstable (delta = -175373942 ns)
JFS: nTxBlock = 8070, nTxLock = 64562

Any ideas?

---

### Post by Feivel on 2009-01-28
> **constable24601 said:**
> I had the same install problem, and followed the advice to hit Esc and select verbose.

The system went through many configuration lines but is now hung much later in the boot process with the Busybox logo again, and the prompt reads

(initramfs)

If the system hang can be identified, the last two lines of the scrolling boot screen read:

Clocksource tsc unstable (delta = -175373942 ns)
JFS: nTxBlock = 8070, nTxLock = 64562

Any ideas?
Maybe one of the smart people will have an idea but that rules out my participation.

---

### Post by constable24601 on 2009-01-29
I finally got a successful wubi install on a standard desktop PC with XP Home, but am running into a brick wall on an IBM T-23 laptop with W2K. I get through all the scrolling verbose screens to the Gnome desktop, but when the ubuntu system goes through its 'checking installation' routine, it stops and requests that I run 'chkdsk /r' in Windows because it claims the NTFS partition is unclean. 'Once that is fixed you should be able to resume the installation. Press OK to reboot'

Multiple reboots, defrags and chkdsks have failed to cure this. Suggestions?

---

### Post by cbowencc on 2009-01-30
Hey, sorry for the late response. I tried verbose, the same thing happened. I believe somewhere along the line it said one of my hard drives was unresponsive or something. It recognized my CD drives and of course the C: drive I installed it on, but still no luck. Any suggestions?

---

### Post by watermd on 2009-02-01
I also have a problem with install under wubi. When I reboot windows xp it only boots into windows and doesn't give me an option for ubuntu. When I go to the boot menu there still isn't any option. I have tried installing ubuntu on both of my hard drives without any change.

---

### Post by Temporary Saint on 2009-02-05
I had the same problem.  What fixed it was rebooting in to Windows and shutting Windows down gracefully (that is, through its menus) and then rebooting into Wubi/Ubuntu.  Worked fine after that.

Steve

---

### Post by pyr0man66 on 2009-02-06
I've had a similar problem with wubi from the 8.04LTS disk I made. When I got to the prompt (where it says type help for a list of commands) I used ctrl-alt-f7 to try to load the desktop, but it didn't load. ctrl-alt-f2 back to the terminal, and I was able to run sudo apt-get (install/upgrade) can't remember which I ran. Seems like maybe for me it's a problem with my nvidia 7950gt.

The system is a shuttle running xp. I had no problems using wubi to install 8.10 on my vista desktop...

---

### Post by davids87 on 2009-02-09
Hi,

I have a small question about Wubi, and didnt want to start a new thread just for that, so I'm writing it here....

I have Vista installed on my C-drive (50MB) and then I also have a free disk, D (250GB), that I'm about to install Ubuntu on. So when i install Ubuntu (with 8 GB Installation Size), can i access the other 242GB i have left on my disk?
I have tried this before but i couldnt find any place to access the rest of the disk. 
Anyone know what i can do?

Thanks!

---

