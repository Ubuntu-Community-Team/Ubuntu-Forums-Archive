---
title: "SMB File copying *really* slow"
date: 2006-10-04
forum: Desktop Environments
---

### Post by gen0 on 2006-10-04
Hi Guys,

I'm kinda new to linux - I have an install of Dapper (upgraded from Breezy) on my laptop and I'm finding copying files to a Samba server on my LAN is really really slow (like 37 mins for 1.2g - or 500k/sec!)  The (wired) eth0 port on my laptop is connected at 100mbit according to mii-tool.  

I am getting good speeds from my laptop using FTP (7mb/sec - but to a different server as my samba server doesn't run have ftp), and also getting much better (not great) speeds copying to my Samba server when I boot my laptop into WinXP (copying 630mb took 5 mins or 2.1mb/sec).

So this doesn't seem to be a problem with the samba server, or a network/driver issue - the problem seems to specifically be the using smb on ubuntu.  The speeds are the same whether I use nautilus or mount the smb share using smbfs.

I've found lots of stuff on the web on tweaking samba servers, but not clients.  Has anyone got any suggestions?

---

### Post by wieman01 on 2006-10-04
I have not tried Windows but my client connection is slow as well... Roughly 900 KB/sec if I am lucky.

---

### Post by mikkelwe on 2006-12-25
Yeah. Copying over SMB is also max 500 KB/S here as well. FTP/inerenet is fine.
I didn't find anything useful on google.

---

### Post by SadaraX on 2006-12-25
I am not sure about copying from or to a Windows Machine, but when copying from or to a Linux machine with another Linux machine I get around 7mb/s when on 100mbit connections.

I normally use the 'scp' command to transfer large files, because I almost always get around 11.5mb/s or 12mb/s when transferring. I am not sure it will help when going between Linux and Windows, but I figured I would mention it.

---

### Post by Youresorock on 2007-07-04
I have the same problem.  I have ubuntu 7.04 running fully up to date.  I'm running Samba 3.0.24.  When I mount my shared volume from XP 64bit I get about 180 - 250KB/s.

I previously had Mac OSX running on the ubuntu machine (identical hardware) and I was able to transfer at about 30MB/s.

I've updated my network drivers to those offered by Realtek, tweaked my smb.conf as suggested allover the interweb, nothing helps a lick.

very fail.

Forgot to mention: both machines have gigabit network cards, with a Cat5e cable inbetween.  No switch.

---

### Post by Youresorock on 2007-07-11
I installed a Linksys Gigabit nic in the machine, and all performance problems went away.

I'm getting between 18 and 40MB/s now.

Strange since I got perfectly good performance out of the onboard with OSX.

I ordered an Intel gigabit nic for a permanent solution.

---

### Post by Vially on 2007-07-13
I also have the issue in 7.04. Around 900KB/s between windows and linux, on 100Mb/s connections AND/OR 1Gbit. I have 4 network adapters on the Linux machine, one is a VIA Rhine II integrated in the VT8237R southbridge, and the other three ones are all RTL8110SC. All are working as they should in XP, but in Ubuntu they are crawling no matter how i setup the network...

---

### Post by Youresorock on 2007-07-13
> **Vially said:**
> I also have the issue in 7.04. Around 900KB/s between windows and linux, on 100Mb/s connections AND/OR 1Gbit. I have 4 network adapters on the Linux machine, one is a VIA Rhine II integrated in the VT8237R southbridge, and the other three ones are all RTL8110SC. All are working as they should in XP, but in Ubuntu they are crawling no matter how i setup the network...

My integrated NIC is an RTL8169.  All the 81xx chipsets use the same driver in linux.  It looks like Realtek pulled the linux driver (for 2.6 kernels).

---

