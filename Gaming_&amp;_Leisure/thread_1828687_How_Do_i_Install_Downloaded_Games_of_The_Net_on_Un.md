---
title: "How Do i Install Downloaded Games of The Net on Unbuntu"
date: 2011-08-19
forum: Gaming &amp; Leisure
---

### Post by KDS997 on 2011-08-19
Im New to Unbutu and Being Trying to Install Games But When i Get to The exe opens and says its not a Software Package Can Please Someone Help!

---

### Post by NovaWasp on 2011-08-19
If it's an .exe file, you probably don't.  Those are Windows files.  They may work with WINE.  WINE is a project that provides compatibility libraries for .exe files.  Some programs work flawlessly, like the Nintendo 64 emulator, Project 64.  Some work with a few issues, like Rosetta Stone not letting you use the microphone.  There is a WINE forum on the main page.  Check there for help on a specific game.

Many games online have Linux versions check the Software Center or the web page for a .deb file.

You can try google with "name-of-game wine" or go to winehq.org.  You may need to find different games to play, dual boot, or go back to Windows, if one of those games is a must have for you.

sorry to not have better news.

---

### Post by KDS997 on 2011-08-19
Ok So Say it i Wanted This Game Called Terreria Would i Have to Get a .Deb File to Be able to install and Would i Simpley Be Able to Right Click Install :D Plz Reply

---

### Post by sliman on 2011-08-19
On the website of the game it said that it was available on steam. You could try downloading PlayOnLinux and then downloading Steam (from the list in PlayOnLinux) to then download the game (from steam)... that is if you already bought the game. (Im kind of new as well, so i dont know if that is the most practical way to go about it) :???:
 

[http://www.playonlinux.com]("http://www.playonlinux.com/")

p.s. You could use VirtualBox

---

### Post by KDS997 on 2011-08-19
Sliman Im Intrested in Virtual Box Could You Tell me What it Does Please

---

### Post by sliman on 2011-08-19
Well, you can install windows on it without having to make a separate partition on the hard drive. You do need a copy of windows and a key in order to install it, but otherwise if you have that, you can run windows and all your programs within Ubuntu, and still have the functionality of having that os on your computer. wine- i guess- installs all of the files that windows uses so that the programs can use that to run. It doesn't run exactly like windows but it just provides what it can. virtual box is like installing it within a predetermined space within the program, although there is a cost of speed and resources within the computer (windows needs some RAM and hard disk space too).

---

### Post by e79 on 2011-08-19
> **KDS997 said:**
> Sliman Im Intrested in Virtual Box Could You Tell me What it Does Please

VirtualBox, as any virtualization product is meant to create and run more than one machine/Operating System (called guests) on the same hardware. As an example, your 'host' would be your actual physical computer, having Ubuntu as operating system; and once VirtualBox would be installed, it would allow you to install Windows XP as a guest (example given) and allow it to use your hardware. No need of dual boot here, the guest (Windows XP in this example) would run in a program window on your Ubuntu desktop.

This way you can try and install Windows only programs, that would otherwise not run under native Linux environment. Be aware of one thing that could be a deal breaker though : 3D video effect are not 'supported' yet and still at experimental stage, so it is not 'every games' that would run into a virtual machine...

You could also give a try to [VMware Player]("http://www.vmware.com/products/player/") to achieve the same.

Hope this helps

---

### Post by KDS997 on 2011-08-19
e79 Would i Be Able  To Run Unbuntu and Windows Vista If So What Requirements Would i Need?

---

### Post by e79 on 2011-08-19
> **KDS997 said:**
> e79 Would i Be Able  To Run Unbuntu and Windows Vista If So What Requirements Would i Need?

Yes you should be able to run a Vista 'Virtual Machine' as a guest on your host running Ubuntu, [U][B]as long as your hardware support virtualization and you have sufficient Ram/Cpu power.
[/B] [/U]
 I suggest you check your BIOS for something like 'Intel (or amd) Virtualization....' and make sure it is at enabled.  Or another way to find out would be to download and install VirtualBox/VMware Player and try to build the Vista virtual machine.

Edit: I forgot to precise somethings in previous posts :

Having a virtual machine, compared to a dual-boot, is giving you access to your Ubuntu AND Windows installations at the same time, per example; but a dual-boot still remains the best options to play certain Windows games.

---

### Post by KDS997 on 2011-08-19
e79 So Wouldnt I Need a Vista Disk Because My Computer is A Acer Aspire it Orginally Came With Vista But Something happened and a file was missing not letting it Boot up If so i Downloaded Virtual Box And Built The Vista Thing How Would i Acess The Vista User?
Please Reply!?:o

---

### Post by e79 on 2011-08-19
In order to build a virtual machine (which has the same steps as installing a fresh copy of Windows on any computers), you would indeed need your Vista DVD with your licence key. If you don't have it you cannot create a virtual machine, as you cannot re-install your Windows on your Acer (unless you have a 'Recovery Partition' - that's a small partition containing everything to reinstate your Windows laptop as it was when you bought it).

BTW in case you didn't know, if you need to recover some files from your previous Windows installation (since you could not boot into it as you said), I suggest you boot your PC with a Ubuntu Live CD, open your Windows partition and _backup all you important files on an external drive/usb._

---

### Post by sliman on 2011-08-20
Whoops.... didn't see the second page..... ignore this post

---

### Post by kunal00731 on 2011-08-29
Hi [KDS997]("http://ubuntuforums.org/member.php?u=1409677"),

In reply to your Question i will tell you that most of the games have either Yourgame.deb packages or Yourgame.sh files  available in the net. So google the game out and download the Linux version of it and install it.

for .deb --> double click and install.
for .sh --> navigate to your disk using terminal, change permission and execute to install.

Happy Gaming.

---

