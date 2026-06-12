---
title: "Will Windows XP reconize my EVGA graphics card like Ubuntu did (VirtualBox)"
date: 2009-04-18
forum: Desktop Environments
---

### Post by FruitRocks on 2009-04-18
I've got running Windows XP SP3 running very smoothly on VirtualBox. Everything is fine, it can detect the sound and my internet card. If I download the EVGA driver for xp, should my vmware installation recognize it, or will it give me errors? Also, when I tried adding a folder to the "shared" section in Virtual Box, I still can't drag and drop the files over from the folder. Why?

---

### Post by CharmyBee on 2009-04-18
Real WinXP machines wouldn't recognize it on the spot out of the box. A driver from nvidia would be required.
As far as VirtualBox goes, it has its own display adapter driver for use in Win2000/XP guest operating systems.
I've never used vmware, but please don't confuse that with virtualbox

---

### Post by prshah on 2009-04-18
> **FruitRocks said:**
> If I download the EVGA driver for xp, should my vmware installation recognize it,

Also, when I tried adding a folder to the "shared" section in Virtual Box, I still can't drag and drop the files over from the folder.

The VirtualBox has it's own VGA driver; you do not need to download the actual VGA driver for your card.

"Sharing" a folder means that it will become available as a samba share, which you can then access in your virtual XP operating system. To access the folder, click Start-Run (in your XP guest OS), then give the command```
net use x: \\vboxsvr\sharename
``` replace the sharename with the name you have given to your shared folder. Now, dragging and dropping to this directory / folder in either the guest or the host OS will make the file available to both.

You need to have VirtualBox guest additions installed and networking enabled for "shared" folders to work.

---

### Post by FruitRocks on 2009-04-18
> **prshah said:**
> The VirtualBox has it's own VGA driver; you do not need to download the actual VGA driver for your card.

"Sharing" a folder means that it will become available as a samba share, which you can then access in your virtual XP operating system. To access the folder, click Start-Run (in your XP guest OS), then give the command```
net use x: \\vboxsvr\sharename
``` replace the sharename with the name you have given to your shared folder. Now, dragging and dropping to this directory / folder in either the guest or the host OS will make the file available to both.

You need to have VirtualBox guest additions installed and networking enabled for "shared" folders to work.

Thanks! has for the graphics card, will my high-permformance games still work in VirtualBox? Like Call of Duty 4/GTA IV?

---

### Post by CharmyBee on 2009-04-18
No, as VirtualBox only passes through OpenGL acceleration to the host system. You mentioned Direct3D games.

---

### Post by prshah on 2009-04-18
> **FruitRocks said:**
> will my high-permformance games still work in VirtualBox? Like Call of Duty 4/GTA IV?

No; there are no "accelerated" functions in the Virtualbox VGA driver (or any virtualization software, for that matter.)

---

### Post by FruitRocks on 2009-04-18
okay; when I run the net use on the run app in windows xp, it brings up a command prompt, throws out a few letters (it closes so fast that I can't see them) then exits. I'm trying to add the /home/username/desktop folder, and the USB folder. it still won't work :(
I've also got all of the guest additions installed, too 

here's the command that I ran: 

net use x: \\vboxsvr/home/cameron/desktop

---

### Post by CharmyBee on 2009-04-18
bring up the command prompt itself first, by
start>run>:
cmd
then do your commands like the net command you've tried.

---

### Post by prshah on 2009-04-19
> **FruitRocks said:**
> 
net use x: \\vboxsvr/home/cameron/desktop

I'm afraid you're going about this in totally the wrong way.

First of all, what is the sharename of the directory you have shared? In VirtualBox, select your virtual machine, then, in "Details" (right hand side) click the "Shared Folders" title, then note the "name" and the "path" in the new window that opens up.

For example, you may have shared a directory "/home/cameron/Desktop", and give it the name "desktop".

In this case, in the guest OS, you will use the command ```
net use x: \\vboxsvr\desktop
``` NOT \\vboxsvr/home/cameron/desktop. The command I mention above will map your shared directory /home/cameron/Desktop to an X: drive in your Windows.

If you have doubts, in your (guest) Windows XP, simply click Start-Run, and give the command```
\\vboxsvr
``` this will show you all shared directories (folders) available to your Windows installation.

---

