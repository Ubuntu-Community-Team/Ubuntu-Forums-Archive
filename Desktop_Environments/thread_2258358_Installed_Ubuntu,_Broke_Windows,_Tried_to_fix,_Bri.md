---
title: "Installed Ubuntu, Broke Windows, Tried to fix, Bricked Computer?"
date: 2014-12-27
forum: Desktop Environments
---

### Post by ryan131 on 2014-12-27
NOTE: By running Boot Repair, I managed to make the Ubuntu install accessible, but Windows still crashes upon boot. I have nudged the outdated information over, so you can ignore the indented text unless you actually need to see it.

Greetings!

I recently installed Lubuntu on my old computer (the one I'm typing this on) and loved it so much I decided to install the full Ubuntu onto my main computer, set to duel-boot with Windows 7. After Ubuntu installed fully and cleanly, I went to boot up Windows and make sure everything was fine on that end, which unfortunately, was not the case. 

When I booted to Windows, I was met with this error:
[http://imgur.com/mSmjwRJ](http://imgur.com/mSmjwRJ)
Upon telling Windows to repair the drive, it failed, and when I rebooted, I got this:
[http://imgur.com/UpxxzYg](http://imgur.com/UpxxzYg)[INDENT=3]Since I am very new to this end of computing and a new Linux user (yes I know that Ubuntu isn't technically Linux anymore), I called up a friend for some help, and he suggested going through the steps on here: [https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)  Specifically, I did the following:
 ```

Windows Vista or 7 or 8

First boot on your Windows Vista/7/8 installation DVD. <snip> When  you get to the Regional settings, select your Location/Keyboard setting  then click next. On the next page, click on "Repair your computer." On the next page, if it finds your Windows installation, make sure it is UNSELECTED before clicking next. Then click on "Command prompt". From there, type in the following 2 commands:


```[/INDENT]
```
[INDENT=3]bootrec.exe /fixboot
bootrec.exe /fixmbr

Now close the two windows and click "Restart." Take out your Windows DVD and hopefully, you will be left with your Windows bootloader.  [/INDENT]

```[INDENT=3]
[/INDENT]
[INDENT=3]
[/INDENT]
[INDENT=3]
[/INDENT]
[INDENT=3]

After following these directions exactly, I rebooted the computer and got this again:
[http://imgur.com/mSmjwRJ](http://imgur.com/mSmjwRJ)

I tried both options, both of which taking me back to the [same blue screen]("http://imgur.com/UpxxzYg")

So we tried completely powering the laptop off (removed the battery and everything), we tried different boot options, with the disk without th disk, etc. and finally we called it off for the night because it was very late (or early)

Danny (my friend) did see that a BIOS update is available, and we both agreed that we will probably be wiping and reinstalling everything (backups ftw.)

Since this computer is specifically for school, and I cannot go without Adobe Creative Cloud (which apparently takes some hacking to get working in Ubuntu), as well as most of my favorite games, I must have Windows 7 on the laptop. If I can get Ubuntu to play nicely with Windows, that would be fantastic, otherwise I can stick with just Windows on there so that I can do what I've been doing.
[/INDENT]

So the questions are:
1. Do you think the data on the Windows partition can be saved, or do I need to wipe everything and start again? (again, the important stuff is backed up)
2. If I need to wipe and start again, is there a better method to set up the multiboot than to install Windows alone, then pop the Ubuntu disk in and install?

Some possibly useful information:
[LIST]
[*]The laptop in question is a Dell Latitude, (I'm not sure if I should share the Service Tag) 
[*]I installed Ubuntu 64bit 14.0.4.1 
[*]While Ubuntu was working on the partition, I left the computer or a few minutes, and it did go into sleep mode, which crashed the process (could be the cause) 
[*]It turns out that Windows 7 won't boot on my old laptop (the one I'm using now) either, but I just left everything as-is so that I'd have a least one usable computer, Windows or not. Honestly, I'm not going to bother fixing that since this is basically used for streaming media/web browsing and not much else 
[*]This second, old laptop mentioned above is a Toshiba Satellite P205 S6237 
[*]At one point, Ubuntu mentioned refusing to send an error report or something because it wasn't a supported build (yet I downloaded the ISO from Ubuntu.com's main downloads page in an effort to get the most standard experience possible) I can't remember the details, and its 2AM, so those might be lost from my brain forever. 
[/LIST]
[INDENT]The specs of my main (bricked) laptop are:
```
Dell Latitude E6530
3rd gen Intel® CoreTM i5-3340M Processor (2.7GHz, 3M cache, Upgradable
to Intel® vProTM technology)
Windows 7 Professional, No Media, 64-bit, English
15.6” HD+ (1600x900) Wide View Anti-Glare WLED-backlit
NVIDIA® NVSTM 5200M (GDDR5 1GB) Discrete Graphic with Optimus
16.0GB, DDR3-1600MHz SDRAM, 2 DIMMS
Light Sensitive Webcam and Noise Cancelling Digital Array Mic
256GB Mobility Solid State Drive
8X DVD+/-RW
Intel® Centrino® Advanced-N 6205 802.11n 2x2 Half Mini Card
``` 
[/INDENT]

Edit 1: I forgot to mention that while trying to get Windows working I lost access to Ubuntu
Edit 2: Here are some pastebin links with info gather using Boot Repair:
Before running the Boot Repair repair: [http://paste.ubuntu.com/9632436](http://paste.ubuntu.com/9632436)
And after: [http://paste.ubuntu.com/9632445](http://paste.ubuntu.com/9632445)

UPDATE: Boot Repair got me back to square one where Ubuntu boots perfectly, but Windows gives me [this blue screen]("http://imgur.com/UpxxzYg").

---

### Post by Rob Sayer on 2014-12-27
If you can boot into ubuntu you can see what partitions are on the HD.  Paste this into terminal ...

sudo fdisk -lu

... and enter your password.  If there's a windows partition it'll be formatted NTFS.  Post the results here, using [CODE] tags.

You should be able to open the windows partition I hope is there and read files.  You may have to change a setting to show it in your file manager ... it's been a while since I've used Unity.  I don't run a dual boot setup anymore but I've copied to/from linux to windows many times.

---

### Post by ryan131 on 2014-12-27
I forgot to mention in the post that while trying to get Windows working, I lost access to Ubuntu

---

### Post by grahammechanical on 2014-12-27
> [COLOR=#000000]Danny (my friend) did see that a BIOS update is available, and we both agreed that we will probably be wiping and reinstalling everything (backups ftw.)[/COLOR]

A BIOS update is most certainly not the answer. Flashing the BIOS, carries a small but significant risk of really bricking the computer. Especially, if we do not know what we are doing. And even if successful it will not fix this problem. 

I suggest that you run Boot Repair. It will produce a report and save it in Pastebin. Post the url to the pastebin location into this thread then we can look through it. At the end of the report is a recommended repair option. Consider what Boot Repair is recommending as fix and decide if you want Boot Repair to try that fix.

By the way, the Windows boot loader does not recognise any other operating systems than Microsoft's operating systems. So, by re-installing the Windows boot loader you lost the ability to load Ubuntu. The real question to ask, is this: When you installed Ubuntu did you instruct the installer to Install Alongside or Erase Disk and Install Ubuntu? You may have wiped Windows off of that machine and that could be why the Windows bootloader cannot load Windows. Does the Boot Repair report show that the Windows OS is on that machine. Or does it only show Ubuntu, which by the way, is still Linux.

Regards.

---

### Post by ryan131 on 2014-12-27
Ok, the only work in the BIOS we've done is changing the boot order, so that's good.

Yes I did tell Ubuntu to install along side Windows

And having run Boot Repair, here are the pastebins:

Before running the repair: [http://paste.ubuntu.com/9632436](http://paste.ubuntu.com/9632436)
and after: [http://paste.ubuntu.com/9632445](http://paste.ubuntu.com/9632445)

I'm going to see if it worked in a few minutes. Gotta get some ice cream before it disappears...

---

### Post by ryan131 on 2014-12-27
Alright, so I'm back to where I started. Ubuntu boots perfectly, but windows [crashes upon boot]("http://imgur.com/UpxxzYg"). The only difference is that there's now [two Windows 7]("http://imgur.com/k2sdAp4") loaders listed, but both crash the same way.

---

### Post by yancek on 2014-12-27
You posted two bootinfoscript pages.  The first one shows windows in the master boot record.  The second shows the Ubuntu Grub in the master boot record.  Which one is correct right now and also, what if anything can you boot now?

>  (yes I know that Ubuntu isn't technically Linux anymore),

I'm not sure about the comment above but, just for clarification, until Canonical/Ubuntu start writing their own kernel Ubuntu is dependent upon Linux and wouldn't exist without it.  Without Ubuntu, Linux would still exist as there are hundreds of other distributions unrelated to Ubuntu and its predecessor, Debian. On the other hand, Ubuntu and its derivatives are obviously the most popular and widely used of the different Linux distributions.

---

### Post by ryan131 on 2014-12-27
Right now Ubuntu is fully-functional, but Windows is failing. The current Master Boot Record is Grub, as far as I can tell.

---

### Post by yancek on 2014-12-27
I don't see any obvious errors in the bootinfoscript.  You have proper entries for windows in fact, two entries and I would think that the sda3 entry would boot.  Not sure what the problem would be.

---

### Post by ryan131 on 2014-12-27
Right now I'm getting ready to wipe and do a clean install. Currently I have the Windows partition mounted and I'm transfering the files to an external hard drive, but while I wait I've been doing some digging and I did find [this article]("http://xavier.robin.name/fr/blog/2012/07/28/installation-of-ubuntu-linux-12.04-precise-pangolin-on-a-dell-latitude-e6530") which got me thinking. Would a 3rd-party bootloader like [EasyBCD]("https://neosmart.net/EasyBCD/") help with my boot issues? Reading the documentation, it doesn't really look like it, unless both OSes decide to boot properly, then I might be able to use that. Or should I partition first, like described [here]("http://lifehacker.com/5403100/dual-boot-windows-7-and-ubuntu-in-perfect-harmony")? Would it make a difference whether I installed either OS from a thumbdrive vs. a disc?

Anyway, that first blog post I linked to is the same model as my laptop, although I have slightly different specs (16GB of RAM, and an Intel i5 3340M) but this is significant because I was looking to see if Dell made the hardware in such a way that dual-booting isn't feasible, and it appears not. I am interested in thoughts on how the things mentioned in that blog post might reflect on my experiences. I just don't have enough experience to comfortably go into some of those changes without a second opinion.

---

### Post by dreamer2 on 2014-12-28
EasyBCD worked for Win7 but not Win8.1. It doesn't ( or didn't) like UEFI. They're supposed to fix it. I've got a system that tri-boots xp, 7, and Fedora on a non-UEFI system and had to work out the proper Windows boot parameters. EasyBCD helped. Watch them close. It is possible without a clean install. This is an UEFI Acer with Win8.1 and 14.04. EasyBCD was not helpful. It all works except I lost access to my shell during a recent upgrade. Things happen in the chaos. I'm lurking for answers.

Good luck,
Gary

---

