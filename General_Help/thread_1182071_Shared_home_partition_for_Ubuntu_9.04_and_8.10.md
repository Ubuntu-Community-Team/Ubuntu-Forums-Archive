---
title: "Shared /home partition for Ubuntu 9.04 and 8.10?"
date: 2009-06-08
forum: General Help
---

### Post by Curbuntu on 2009-06-08
When I installed Ubuntu 9.04 on my 5-year-old Compaq Presario R3399CL laptop, I thought I'd experiment with partitioning just a bit, leaving room for two Ubuntu versions (9.04 and 8.10) so that I could dual-boot the "old" and "new" versions, as well as a **separate partition for /home**:

[CENTER] [ATTACH]116919[/ATTACH]
[/CENTER]
 
[If the attachment doesn't work, that's:

[LIST]
[*] /dev/sda1/ = 9.04 root (11.18 Gb)
[*] /dev/sda2/ = extended partition (100.61 Gb)
[*] /dev/sda5/ = 8.10 root (and 8.10's "/home"; 11.18 Gb)
[*] /dev/sda6/ = /home for 9.04 (and, I hope, 8.10, once this message gets answered; 85.71 Gb)
[*] /dev/sda7/ = linux-swap (3.72 Gb)]
[/LIST]
 
I installed 9.04 first.  Somehow when I installed 8.10, I failed to discover the means to tell the installer that I already had a /home partition, so it assumed it should include 8.10's /home in /dev/sda5.

I have tried for weeks -- unsuccessfully -- to be able to remote into this laptop within my home network from any other machine in the house (either Ubuntu 8.10 running vinagre or two machines running flavors of that other O$).  Remote'ing/VNC'ing to the laptop works fine when the laptop boots to 8.10, but fails miserably in 9.04.  So, I'd like to fall back to 8.10, making it the default in the GRUB boot up.   But...

** I can't figure out a way to tell the existing 8.10 installation that it should be using the sda6 /home partition for its /home.**  I can reinstall 8.10 if necessary (it would be good to know what option I missed anyhow), but it would be nice to just change a setting in 8.10 and be done with it.

Any help on this would be appreciated!  

P.S.: If you can solve the Remote Desktop failure in 9.04, so much the better.  FWIW, all machines in the house can PING each other (including 9.04) and all can make it out on the 'Net.  The 9.04 boot can remote any other machine in the house.  FYI, the 9.04 partition is 64-bit, while the 8.10 partition is 32-bit, if that matters.  The laptop connects to the network wirelessly, using a Broadcom B43xx and the Ubuntu-recommended driver.  All attempts to try to reach the 9.04 machine get the following error message (on the client):

[CENTER] [ATTACH]116923[/ATTACH][/CENTER]

---

### Post by 67GTA on 2009-06-08
You have to choose the "manual" installer option. Then tell the installer when you edit your /home partition to mount it as /home, but not to format it. Having said that, you can't use the same /home partition between distro versions. You will wind up with buckets of problems because of application version troubles and permission problems.

---

### Post by Curbuntu on 2009-06-08
67GTA,

Thanks for the quick response.

> **67GTA said:**
> You have to choose the "manual" installer option.

Yes, the manual option was what I used to partition 9.04, saving space for 8.10.  I must have used the manual for the 8.10 install (not certain), but...

> **67GTA said:**
> Then tell the installer when you edit your /home partition to mount it as /home, but not to format it. 

Ah, ***that's*** the part I didn't figure out.  If it's not formatted, then what does the Ubuntu installer do when it gets to the part of the script that writes the /home info to the /home partition -- just skip that part of the process?

> **67GTA said:**
> Having said that, you can't use the same /home partition between distro versions. You will wind up with buckets of problems because of application version troubles and permission problems.

Hmm.  That makes sense, now that you point it out.  I was thinking mainly in terms of the data folders (e.g., .odts, mp3s, etc.), but I hadn't considered the data in the .hidden folders, which *would *be version-specific.  That brings up two follow-on questions:


[LIST=1]
[*]Would the setup work as I describe if I were dual-booting equal versions like Ubuntu 9.04 and Kubuntu 9.04?  And...
[*]In my current setup (i.e., Ubuntu 8.10 and 9.04) is there some work-around (e.g., yet another partition, shared for non-hidden data)?
[/LIST]
Also, any thoughts on Remote-Desktop problem?  If that were fixed, I wouldn't have to consider keeping 8.10 at all.

---

### Post by 67GTA on 2009-06-08
> Ah, ***that's*** the part I didn't figure out. If it's not formatted, then what does the Ubuntu installer do when it gets to the part of the script that writes the /home info to the /home partition -- just skip that part of the process?

It just sets it up to be mounted as /home in /etc/fstab, but leaves any data in the partition intact. 

> Hmm. That makes sense, now that you point it out. I was thinking mainly in terms of the data folders (e.g., .odts, mp3s, etc.), but I hadn't considered the data in the .hidden folders, which *would *be version-specific.  That brings up two follow-on questions:


[LIST=1]
[*]Would the setup work as I describe if I were dual-booting equal versions like Ubuntu 9.04 and Kubuntu 9.04?  And...
[*]In my current setup (i.e., Ubuntu 8.10 and 9.04) is there some work-around (e.g., yet another partition, shared for non-hidden data)?
[/LIST]


I create a folder called "Media" that I can put all of the data folders inside of like Music, Videos, Documents, etc. This way any distro can use this folder without having to worry about hidden settings and permissions. That won't really help you in this situation though.
If the versions are the same, it won't matter if you have the same username and passwords on both installations. KDE and Gnome use different config files, but some are the same. You still might run into an occasional problem. Have you thought about virtualbox? That might be a viable solution. What trouble are you having with remote desktop?

---

### Post by SoCalChris on 2009-06-08
Couldn't each version have it's own home folder, and then the Documents/Desktop/Music/Videos/etc folders all be symlinks pointing to common directories?

For example, have all of the folders actually stored in the home partition that 8.10 uses, and then have the directories as symlinks in the 9.04 home partition pointing to the directories in the 8.10 partition.

That way, each version would have it's own home folder to store dot files in without creating problems, and you'd also have your other folders synchronized between the two installations.

---

### Post by Curbuntu on 2009-06-08
> **67GTA said:**
> Have you thought about virtualbox? That might be a viable solution.

Yes, actually, I use VB to run XP Home (mainly for extended-relatives support purposes).  But I set up the dual-boot situation because 9.04 was a new release, and therefore an untried entity.

> What trouble are you having with remote desktop?Logging into an Ubuntu machine via VNC [either RealVNC or uVNC from Windows machines] or vinagre [from an Ubuntu machine] used to be easy.  Setting up the "server" is easy, too (although it's strange that 9.04 doesn't have a second tab in its Remote Desktop setup dialog like previous versions of Ubuntu did).  But try as I might, I can't make it work in Ubuntu 9.04-64.  It turns out, I couldn't do it in Xubuntu 9.04-32 on an old "beater" machine, either.  It doesn't matter what setting I do or don't use; even deliberately setting it up without a password doesn't buy me anything.  Yet this machine can receive connections quite handily when I boot it into 8.10.

---

### Post by Curbuntu on 2009-06-08
> **SoCalChris said:**
> Couldn't each version have it's own home folder, and then the Documents/Desktop/Music/Videos/etc folders all be symlinks pointing to common directories?

For example, have all of the folders actually stored in the home partition that 8.10 uses, and then have the directories as symlinks in the 9.04 home partition pointing to the directories in the 8.10 partition.

That way, each version would have it's own home folder to store dot files in without creating problems, and you'd also have your other folders synchronized between the two installations.

I don't have enough experience to know if there are any downsides to your proposal, but it would seem to make sense.  Symlinks, I assume, are more or less like .lnk files in Window$?  That is, are they file or folder representations that actually "point" to the real file or folder elsewhere?  

Any pointers about making symlinks?

---

