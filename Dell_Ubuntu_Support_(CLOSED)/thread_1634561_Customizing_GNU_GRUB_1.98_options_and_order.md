---
title: "Customizing GNU GRUB 1.98 options and order"
date: 2010-11-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dmalosh on 2010-11-30
[FONT=Arial][SIZE=2]Hi all!

I am a newbie to Ubuntu (I am a Windows and Mac user), and thus a newbie to the forums.  I tried searching for my question(s) before posting but didn't see exactly what I was looking for.  (Though I'm sure my answers are in here somewhere.  I apologize in advance if my questions are seemingly answered on a daily basis here.)

I need to run Linux for a program we use at work, and although Fedora was suggested, I chose Ubuntu because it seemed easier to set-up dual boot options.  Fedora wanted me to make the partitions, etc. whereas Ubuntu makes all that way easier.

We need a computer that permits us to use both Linux (Ubuntu v10.10) and Windows XP (SP3).  As of right now, dual booting works very smoothly.  I am running GNU GRUB version 1.98.

I am wondering if there is a way to omit boot options from GNU GRUB.  I'm sure there is, and I'm just using the wrong words in my searches.

Here are my options at boot-up...[/SIZE][/FONT][SIZE=2]

[/SIZE][FONT=Courier New][SIZE=2]Ubuntu, with Linux 2.6.35-23-generic
Ubuntu, with Linux 2.6.35-23-generic (recovery mode)
Ubuntu, with Linux 2.6.35-22-generic
Ubuntu, with Linux 2.6.35-22-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Microsoft Windows XP Professional (on /dev/sda2)[/SIZE][/FONT][SIZE=2]
[/SIZE][FONT=Arial][SIZE=2]
How can I omit the third and forth options?  I am assuming that they are boot options for a slightly older release of Ubuntu (is it the kernel's version?), thus the "[/SIZE][/FONT][FONT=Courier New][SIZE=2]...22-generic[/SIZE][/FONT][FONT=Arial][SIZE=2]" versus the "[/SIZE][/FONT][FONT=Courier New][SIZE=2]...23-generic[/SIZE][/FONT][FONT=Arial][SIZE=2]" above.  I could be wrong, but I suspect they are somewhat redundant entries.

I would also consider removing the two entries for "[/SIZE][/FONT][FONT=Courier New][SIZE=2]Memory test[/SIZE][/FONT][FONT=Arial][SIZE=2]," but I worry that I might regret that some day.  As for now I am uncertain of their value.  The bottom line is, I want to minimize the number of options as the people who will be using this PC will not be all the tech-savvy.  I suspect that something as simple as dual boot options could be a nasty speed bump for them.

Also, is there a way to change the name as it appears?  For example, could I change [/SIZE][/FONT][SIZE=2]"[/SIZE][FONT=Courier New][SIZE=2]Microsoft Windows XP Professional (on /dev/sda2)" [/SIZE][/FONT][FONT=Arial][SIZE=2]to simply [/SIZE][/FONT][FONT=Courier New][SIZE=2]"Microsoft Windows XP[/SIZE][/FONT][FONT=Arial][SIZE=2]"?  Or how about "[/SIZE][/FONT][FONT=Courier New][SIZE=2]Ubuntu, with Linux 2.6.35-23-generic" [/SIZE][/FONT][FONT=Arial][SIZE=2]to just [/SIZE][/FONT][FONT=Courier New][SIZE=2]"Ubuntu"[/SIZE][/FONT][FONT=Arial][SIZE=2]?

I would be most grateful for any help I can get.  Thanks in advance!
-Dan M.
[/SIZE][/FONT]

---

### Post by oldfred on 2010-11-30
For the best info set the link to drs305's grub pages.

Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)

How to: Create a Customized GRUB2 Screen that is Maintenance Free.
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

OR Partial Custom menu:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

One way to fix the descriptions is to move the windows entries to 40_custom and edit at will.

Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit :
gksudo gedit /etc/grub.d/40_custom

after all changes
sudo update-grub

---

