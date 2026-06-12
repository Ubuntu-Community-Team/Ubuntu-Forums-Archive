---
title: "VMware a sufficient condom for WinXP? Or AntiVirus still needed"
date: 2007-04-18
forum: Desktop Environments
---

### Post by Jhongy on 2007-04-18
I'm moving from a dual-boot Ubuntu/WinXP system to full-Ubuntu. 

What has mostly been preventing me from doing so thus far has been my wife, as well as a WinXP program or two that I need. However, dual booting is a hassle, and I've discovered the advantage of virtualisation.

I've set up an XP VM using VMware Workstation... and it's pretty snappy. It has its own system disk, but acceses several shared Linux folders through the VMware "network" interface.

I figured that, since the VM has direct access to these shares, it should be running antivirus software... right? I know Win32 viruses won't be able to spread to Linux, but I don't want them to append themselves to anything on the file stores which could compromise someone else.

The problem is that, while the VM runs quite smoothly (I give it around 700MB of memory to play with), the AV (Norton AV 2007) slows the machine to molasses. I actually paid for this piece of yellow cr*p... it has a ridiculous animated icon, a big flashy, vista-esque interface, with very few options... and it slows the boot-up process significantly.

So, I was thinking, is this really necessary??? My only real concern is the write access XP has to those shares, as the system disk can easily be restored from a snapshot. If it is a must, can anyone recommend something lighter and less resource-intensive than the giant yellow wasteland of NAV?

---

### Post by kvonb on 2007-04-18
When I was a Windows slave, I used AVG anti-virus.

It's free and I have been very happy with it's performance over the years.

I believe you get it from free.grisoft.com.

I run XP in a vmware session and don't bother with any virus/spyware/firewall software at all.  Although I really don't use it that much to be bothered, and I don't install suspect things on it or use it for e-mail either.

You could always simply make a copy of the actual vm file each week, then if something went wrong, just copy it back.

---

### Post by Jhongy on 2007-04-18
Thanks... I'll look into that one. Any other suggestions? Speed is of utmost importance.

> **kvonb said:**
> 
I run XP in a vmware session and don't bother with any virus/spyware/firewall software at all.  Although I really don't use it that much to be bothered, and I don't install suspect things on it or use it for e-mail either.

You could always simply make a copy of the actual vm file each week, then if something went wrong, just copy it back.

I'm not so bothered about the XP system files... VMware workstation een provides the option to start from the same snapshot each time, so I could effectively make the image static. But I *do* want to provide write access to a couple of folders outside of the VM, and that is what's really worrying me.

We're fairly security conscious, and well firewalled, but my wife has to use several ActiveX controls in IE as  a matter of course... I don't want to compromise any of the shared data.

---

### Post by hardyn on 2007-04-18
i use AVG on my windows partition... its actually quite good, and as mentioned above free.  they even give you almost daily virus updates.  they make it a little trickey to find on the website, but it is there... googleing 'free avg' is usually quicker.

---

### Post by kvonb on 2007-04-18
We're fairly security conscious, and well firewalled, but my wife has to use several ActiveX controls in IE as a matter of course... I don't want to compromise any of the shared data.

Yes, any file or folder that is write enabled for your VMware Windows will still have the same vulnerabilities, even if it's on a Linux file system.

So if a virus wanted to delete all your files, and it had write access to a shared folder, then technically it could do so.

Instead of doing a straight file share, you could share a folder through "samba", you can make it read/write so that the VM and also other computers on your home network can access it/them, but make it require a password for write operations.

So each time you, your wife, or a virus wanted to write to or delete a file, it would ask for a password.

That would give a little more protection, but it may be a pain in the rear always typing in a password!

Just ask if you wish to try that, I can help you set it up.

Regards, KEv :)

---

### Post by Jhongy on 2007-04-18
Thanks...

I think that might be too cumbersome. I intend to set the "desktop" folder and everything in "my documents" to point to Linux shares (shared through VMWare Worksation). 

The idea is that all her files will be available on the host computer -- which I intend to be a faster, better and more useful experience for her in the long run. (With the full intention of converting her in the long run). However, making Windows more cumbersome will just turn her away from the deal altogether.

---

