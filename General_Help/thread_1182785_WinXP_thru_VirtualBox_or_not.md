---
title: "WinXP thru VirtualBox or not?"
date: 2009-06-09
forum: General Help
---

### Post by joelop on 2009-06-09
Hi Guys,

I have a doubt: In my laptop I have installed Ubuntu as main OS and WinXP. Now I've read that with VirtualBox one doesn't need to reset their OS in order to work with a windows application, which is great but if I install Virtualbox now I think I will have problem of space (I have a 50Gb HD, 25Gb for each OS) so the questions are:

-Is it worth keeping WinXP as a secundary OS in my HD if I could use it with VirtualBox?

-When I bought my laptop (DELL) WinXP came pre-installed; if I format my HD and don't install WinXP -just Ubuntu- will I lose WinXP forever? (I don't have the original WinXP CD, just the one Dell gives away for preinstalled machines)

Read you later! ;)

---

### Post by whoop on 2009-06-09
> **joelop said:**
> 
-Is it worth keeping WinXP as a secundary OS in my HD if I could use it with VirtualBox?

that depends what you use windows xp for. Virtual Box is not good for gaming for instance...
> **joelop said:**
> 
-When I bought my laptop (DELL) WinXP came pre-installed; if I format my HD and don't install WinXP -just Ubuntu- will I lose WinXP forever? (I don't have the original WinXP CD, just the one Dell gives away for preinstalled machines)

Well if you format your hd you will need the cd to if you wish to reinstall windows. On the other hand you could make an image of your hd and store that so you can later put the image back on your hd.

---

### Post by konqueror7 on 2009-06-09
also a thing to note is, is your hardware capable of running a VM? because it would be a waste if you can't run any more apps just by launching th VM...

also, you mentioned that you don't have a XP cd (you said it was preinstalled), the problem is how will you install XP in VirtualBox now, take a look at VMware as i think it supports converting you exsisting OS installation and converts it into a virtual hard drive...

---

### Post by joelop on 2009-06-09
> **whoop said:**
> [quote=joelop;7427289]
-Is it worth keeping WinXP as a secundary OS in my HD if I could use it with VirtualBox?
[/code]
that depends what you use windows xp for. Virtual Box is not good for gaming for instance...


No, I don't game at all.

---

### Post by joelop on 2009-06-09
> **konqueror7 said:**
> also a thing to note is, is your hardware capable of running a VM? because it would be a waste if you can't run any more apps just by launching th VM...

also, you mentioned that you don't have a XP cd (you said it was preinstalled), the problem is how will you install XP in VirtualBox now, take a look at VMware as i think it supports converting you exsisting OS installation and converts it into a virtual hard drive...

Well, as I said I don't have an origial WinXP cd, just_ the one given by Dell_, the one I've been using all this years when I needed to format and re-install WinXP. I've heard (dunno if it's true) that in pre-installed equipments they (manufacturers) keep a hidden space in your HD for info, files, etc in case you need to format and re-install WinXP...

---

### Post by aysiu on 2009-06-09
You don't need 25 GB for each OS. Maybe you need that space for personal files (photos, music, movies), but not for the OSes.

With some basic programs, Windows XP can be as small as 10 GB. A default Ubuntu installation is less than 3 GB, and it comes with a ton of software already installed.

Unfortunately, I don't think the Dell XP CD will work as a VirtualBox installation CD. So if you were to virtualize, it would be a virtual Ubuntu inside of XP. How about doing a Wubi dual-boot? Then you won't have to mess with partition sizes or worry about a lack of RAM affecting performance.
[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

---

### Post by joelop on 2009-06-09
> **aysiu said:**
> How about doing a Wubi dual-boot? Then you won't have to mess with partition sizes or worry about a lack of RAM affecting performance.
[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

Well, actually I first tried Ubuntu with **Wubi** but I had some problems [you can read here]("http://ubuntuforums.org/showthread.php?t=1169734") and some people said it could be because of Wubi... :o

---

### Post by aysiu on 2009-06-09
> **joelop said:**
> Well, actually I first tried Ubuntu with **Wubi** but I had some problems [you can read here]("http://ubuntuforums.org/showthread.php?t=1169734") and some people said it could be because of Wubi... :o
That doesn't seem like a standard Wubi installation. Did you try to install it to an external USB drive?

---

### Post by CaptainEvilStomper on 2009-06-09
> **joelop said:**
> Well, as I said I don't have an origial WinXP cd, just_ the one given by Dell_, the one I've been using all this years when I needed to format and re-install WinXP. I've heard (dunno if it's true) that in pre-installed equipments they (manufacturers) keep a hidden space in your HD for info, files, etc in case you need to format and re-install WinXP...

Occasionally they do that in lieu of giving you the install CD. Since you said they gave you an install disc I'd say they didn't install a hidden restore partition, but if you open up GParted it'll show you all the partitions on your hard drive, including the hidden one if it's there. If you don't have it installed open up a Terminal window and type "sudo apt-get install gparted" (without the quotes) and type in your password when it asks for it. Then run it with "gksudo gparted" (again, no quotes). It also appears in one of the menus as "Partition Editor" so you can run it from there, but I honestly don't remember where it is (I think it's either Applications > System Tools or System > Administration).

In any case, you're going to need at least a 2 GHz dual-core processor, 2 GB of RAM, and a decent integrated GPU if you want to run VirtualBox - otherwise it's most likely going to incredibly slow. There is an option to create a virtual hard drive that points to an actual partition on your hard drive, which you can read about in the user manual: [http://www.virtualbox.org/manual/UserManual.html#rawdisk](http://www.virtualbox.org/manual/UserManual.html#rawdisk) If you screw it up you can destroy all the data on that partition, though, so make sure you have everything backed up to an external drive if you want to try this.

You can also use nLite to slim down the XP install disc and get rid of unnecessary drivers & software, disable certain features, tweak your settings, remove aspects of the OS you don't want, remove languages and keyboards you don't use, etc. Once you've done that XP should run a lot smoother in a virtual machine compared to a full install, and it should only use a few GB on your hard drive.

---

### Post by joelop on 2009-06-09
> **aysiu said:**
> That doesn't seem like a standard Wubi installation. Did you try to install it to an external USB drive?

No, I installed it in my HD. The story with the USB HD's came later and people said it happened due to having Ubuntu installed through WinXP with Wubi.

---

### Post by Chris Musampa on 2009-06-09
> **CaptainEvilStomper said:**
> 
In any case, you're going to need at least a 2 GHz dual-core processor, 2 GB of RAM, and a decent integrated GPU if you want to run VirtualBox - otherwise it's most likely going to incredibly slow. 
That obviously depends what he wants to use XP for.  The laptop I'm posting from is a 1.6GHz Celeron with 1GB RAM and Intel 915 graphics, I occasionally use a virtual XP (512MB RAM) to run TVants or TVU to watch football games no problems whatsoever.

---

### Post by uidb4056 on 2009-06-09
> **joelop said:**
> Hi Guys,

I have a doubt: In my laptop I have installed Ubuntu as main OS and WinXP. Now I've read that with VirtualBox one doesn't need to reset their OS in order to work with a windows application, which is great but if I install Virtualbox now I think I will have problem of space (I have a 50Gb HD, 25Gb for each OS) so the questions are:

-Is it worth keeping WinXP as a secundary OS in my HD if I could use it with VirtualBox?

-When I bought my laptop (DELL) WinXP came pre-installed; if I format my HD and don't install WinXP -just Ubuntu- will I lose WinXP forever? (I don't have the original WinXP CD, just the one Dell gives away for preinstalled machines)

Read you later! ;)

I would suggest you a test before going ahead because is not sure you can install XP from the CD you have inside a VirtualBox. The test needs that you have a USB disk or pendrive with at least 4GB.


[LIST=1]
[*]Format your USB as Ubuntu File System.
[*]Install Virtualbox from SUN repositories not Ubuntu OSE version
[*]Create a VM for XP with the disk file in the USB drive
[*]Test to start it with your CD to see if you can install XP with it inside virtualbox machine
[/LIST]
If you can then you can delete the new created virtual machine, delete or reformat the windows partition and use the space for store your new VM disk and install XP on it.

---

### Post by nmaster on 2009-06-09
These are really great guides if anyone needs them.

[http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux](http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux)

[http://lifehacker.com/5204434/the-beginners-guide-to-creating-virtual-machines-with-virtualbox](http://lifehacker.com/5204434/the-beginners-guide-to-creating-virtual-machines-with-virtualbox)

---

### Post by nmaster on 2009-06-09
Somewhat related question: Has anyone tried running Skype through a Windows XP VirtualBox?

There are unresolved bugs with it on Jaunty, and I thought it might be a good option.  Let me know if anyone has already tried it.

---

