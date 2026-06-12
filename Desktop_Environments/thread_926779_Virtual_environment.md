---
title: "Virtual environment"
date: 2008-09-22
forum: Desktop Environments
---

### Post by ashrafkhanzaade on 2008-09-22
greetings

looking for the most idiot proof of booting / running my existing XP install from within ubuntu 8.04 preferably using software that comes packaged with the distribution. currently using a dual-boot environment. half of the disk belongs to MS and we cannot interfere with that partition.

need advice with regards to how this would be done please.

---

### Post by snowpine on 2008-09-22
> **ashrafkhanzaade said:**
> greetings

looking for the most idiot proof of booting / running my existing XP install from within ubuntu 8.04 preferably using software that comes packaged with the distribution. currently using a dual-boot environment. half of the disk belongs to MS and we cannot interfere with that partition.

need advice with regards to how this would be done please.

Hi there, your easiest option is to set up a dual boot, so that you can choose between Ubuntu and Windows each time you boot. It's really easy to set this up when you install Ubuntu; all you need to do is choose "Resize existing partition and install Ubuntu to the free space" when you get to the partitioning stage. The installer will install the necessary Grub options for you. This is what I do at home, and it works flawlessly.

Virtualizing your existing Windows partition is not for the beginner. You should start by educating yourself about virtualization: [http://ubuntuforums.org/showthread.php?t=582729](http://ubuntuforums.org/showthread.php?t=582729)

Then, once you understand the basics, here is your next step: [http://www.vmware.com/download/converter/](http://www.vmware.com/download/converter/)

I've never done it frankly so that's all I can really tell you. :)

(edit): ps Another option that is quite popular, but that I haven't personally tried, is to install Wubi, which lets you run Ubuntu as an application in Windows. It is sort of the opposite of what you're trying to do, but much, much easier. :)

---

### Post by Lacasito on 2008-09-23
Nowadays I'm using Virtualbox to run XP and Ubuntu 8.04 as guests on my Ubuntu 7.10 and both work fine

It's a solution if you need XP or you want to try on other distros with neither installing anything nor partitioning

---

### Post by anars on 2008-09-23
I can vouch for the speed and stability of VirtualBox. I've used QEMU before as a stand-alone entity, and VirtualBox encapsulates all of that brilliant functionality into an easy-to-use GUI.

I'm running Windows XP and Windows Vista on seperate virtual machines in VirtualBox for work, and it's brilliant. I'm not noticing I am working using a virtualized environment, ever. The applications I'm using are Visual Studio 2008, MS SQL Server 2005/2008 etc., and they're running smooooothly.

Give it a try at least.

---

