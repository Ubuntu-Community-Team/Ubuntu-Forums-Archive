---
title: "Generic install on Inspiron 1720 - problems"
date: 2009-02-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by daveh551 on 2009-02-20
I have completed an Ubuntu install from the generic download (from ubuntu.com) onto a 9-month old Inspiron 1720 laptop that is set up to triple boot (Vista, Win XP, and now Ubuntu).  Whil I am a 30-year software engineering veteran, I've spent the last 15 years in Microsoft world, and I'm a Linux newbie. The installation was generally successful, after getting over some learning curves, but I have the following residual problems:

a) (Main one) Sound doesn't work.  I mean, I think I can almost hear something when it's playing. lspci lists the intel sound chip, and amixer thinks it's playing things at full volume, but it's just not there. 

I've googled it, and found a large number of posts related to the problem, but they give no consistent solution, and often contradict each other.  I have tried a few of them with no effect. I have NOT yet tried re-building the alsa source, but I am not afraid to if that's what it takes.

b) After I enabled the proprietary Broadcom driver, the wireless network works fine.  However, I have the NIC port disabled in the BIOS.  If I enable it, then when I reboot Ubuntu, the wireles port no longer works.  Since I rarely use the NIC port, that's more annoyance or a head-scratcher than a serious problem.  I don't know if the NIC port actually works or not, just that it makes the Wireless port not work.

c) My laptop has dual 320G drives.  The second one is not showing up in computer explorer.  All my Microsoft partitions (both NTFS and FAT - 6 partitions besides the Linux partition) on the first drive are showing up.  And there is a disk icon labeled simply "SCSI Drive".  If I double-click it, a message box opens saying "Unable to mount location".  I don't know if this is the second drive or not, nor what to do to be able to mount it.

I did stumble across the Dell reinstallation media for Intrepid, and downloaded and burned it.  But I clearly DON'T want to wipe my disk (besides the time spent setting up the partitions and installing the other software, there's a lot of personal and work related data stored on thes disks), so I didn't continue with installation.  I'm sure that the reinstallation media must have some files that are more relevant to my hardware than the generic installation that I did. Does anyone know of a way to make use of that reinstallation disk, but confine it to my Ubuntu partition?

Also, their notes made reference to updates that may have become available after that media was release.  How do you go about finding/getting/installing those updates (again, this from a linux newbie).

Any help would be appreciated. Thanks in advance.

---

### Post by Mordac85 on 2009-02-24
OK, I'll try to help.

Sound - I'd try the backports solution in [http://ubuntuforums.org/...t=691946]("http://ubuntuforums.org/showthread.php?t=691946")

NIC - Which Broadcom driver did you use and are you using NetworkManager to automagically configure your network or did you do so manually?

Missing drive - You need to mount this to access it, but if you don't know which one it is it can be difficult.  You can check the /dev folder for which block device it is or run dmesg in the console to see what it's seeing.

Dell restore CD - If my experience w/the Windows versions are any indication, I don't think this can be easily modified for your use and it is most likely identical to what you downloaded.  It may however have extra drivers and such so it's worth poking around to see what;s there.

---

