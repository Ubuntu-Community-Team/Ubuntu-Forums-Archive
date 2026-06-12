---
title: "Desktop Environment problems, more to come?"
date: 2009-05-16
forum: Desktop Environments
---

### Post by mntokman on 2009-05-16
Hello all fellow Linux users, 

I first started to use linux with red hat and windows for a while. Recently I installed Xubuntu on my Windows OS. For some stupid reason I wanted to format my computer to install Linux and Windows on two different partitions. I switched from Gnome to KDE environment and that is when all the problems started. 

For example:

* My wireless network does not work, after long hours I found forums saying that my wireless card is actually bugged....I installed 8.10 Kubuntu and I had Xubuntu 8.04 I think. 

* Also I learned that Audio CDs cannot be played on modern Linux OS...

* If I extend the borders of a word file and try to open .docx/doc files on Linux, the format is all messed up and requires long reformating. 

One of the reasons why I switched to Linux is to increase my productivity but I have to fix and do things to make certain things work. What is the point of using Linux if this will be the case all the time?
 
And what is the difference between LTS and other releases?

Never had an Apple but I think it is about time to get one and forget about linux and windows all together. 

Any suggestions?

Michelle

---

### Post by kpkeerthi on 2009-05-16
> **mntokman said:**
> 
* Also I learned that Audio CDs cannot be played on modern Linux OS...

This is not true.

> **mntokman said:**
> 
One of the reasons why I switched to Linux is to increase my productivity but I have to fix and do things to make certain things work. What is the point of using Linux if this will be the case all the time?
May be you are unlucky. Linux has found a permanent place in millions of computers.
 
> **mntokman said:**
> 
And what is the difference between LTS and other releases?

[https://wiki.ubuntu.com/LTS]("https://wiki.ubuntu.com/LTS")

> **mntokman said:**
> 
Never had an Apple but I think it is about time to get one and forget about linux and windows all together. 

Use what works for you.

**Suggestion: **Try with a clean Jaunty (GNOME) install

---

### Post by mntokman on 2009-05-16
how do you play Audio CDs on Kubuntu? you say it is not true but you do not provide any solutions and leave a generic answer, which is "use what works best for you"

---

### Post by t0mppa on 2009-05-16
If your wireless chip worked on Windows earlier, it should work on Linux as well. If it's one of the trouble childs (where the manufacturer hasn't bothered to provide any open source versions), might not be easy to get it to work, but they all tend to work sooner or later.

Judging from a quick search the audio CD thing is a bug that happens sometimes on KDE apps, not a linux-wide problem. Maybe you should just try reverting back to Gnome, I've yet to see KDE provide any spectacular differences - only a more Windows like GUI for an easier transition to Linux.

[QUOTE=mntokman]One of the reasons why I switched to Linux is to increase my productivity but I have to fix and do things to make certain things work. What is the point of using Linux if this will be the case all the time?[/QUOTE]

Things don't break on Linux all the time, once you get your system set up, it'll stay up and running rather nicely. OS upgrades naturally have a chance to cause further trouble, but that's the same with every OS.

As for the Mac vs. Linux vs. Windows issue, this is the way I see it:[LIST]
[*]Macs are for elitists and have a neat OS and good support for drivers. Drawback being that they cost 1.5 - 2 times more than other computers, but if you have the spare cash and want an easy to use and properly working system, go for it.
[*]Linux offers a nice OS and is free, but hardware manufacturers haven't caught up with the hype, so drivers can be a b*tch to set up. If you have a tech savvy friend to help with that or want to learn more about OS intrinsics or have the possibility to handpick your hardware, so that it's Linux friendly, then it's a viable choice.
[*]Windows is unpopular with geeks, but still by far the most popular (though I suspect it's losing users all the time) choice and has good hardware support, plus perhaps the best collection of software, since it also has most firms providing software for it.
[/LIST]

---

### Post by BZF on 2009-05-16
[SIZE=1][COLOR=Blue]just reinstall the cd cus u will have even more problems using apple cus its absolute crap, that means something just happened when installing and cd's always work unless you didn't get all the drivers[/COLOR][/SIZE]

---

### Post by mntokman on 2009-05-16
Audio CD still does not play, I can play mp3 and videos now. 

Wireless still does not work, I had a thread about it and the link is below. If you have any suggestions let me know please. 

[http://ubuntuforums.org/showthread.php?t=1155896](http://ubuntuforums.org/showthread.php?t=1155896)

---

### Post by cariboo on 2009-05-16
We need more info, before we can help you solve your problems.

[list]
[*] Do you get an error message when you insert a music cd?
[*] What is the make and model of your computer?
[*] What wireless chipset does youe wireless device have?
[/list]

For a start, go to Start-->Applications-->Utilities-->Terminal and type:

```
lspci
```

This command will list your hardware, please paste the output in your next post.

---

### Post by kpkeerthi on 2009-05-17
> **mntokman said:**
> how do you play Audio CDs on Kubuntu? you say it is not true but you do not provide any solutions and leave a generic answer, which is "use what works best for you"

Looking at your original post, it appears that you were not looking for any help and just expressing your opinion on Linux.

---

### Post by andrea000 on 2009-05-17
As far as playing a cd read [this]("http://linux.about.com/od/kubuntu_doc/a/kubudg25t02.htm") a good Google search will pull up more
and you may pull up some information on your wireless card to.

---

### Post by ugm6hr on 2009-05-17
I would suggest:

Start over with a frsh install of either 8.04LTS or 9.04 (I suggest the latter, since it will be supported until the next LTS at 10.04 anyway, and seems pretty stable to me).

Once done, try to resist the temptation to meddle with the workings.  The reason OSX is so reliable is that it does not allow you to change much; freedom to customise means freedom to mess up.

If you still have problems, post back one problem per thread.

---

### Post by XubuRoxMySox on 2009-05-17
> **t0mppa said:**
> 

Judging from a quick search the audio CD thing is a bug that happens sometimes on KDE apps, not a linux-wide problem. Maybe you should just try reverting back to Gnome, I've yet to see KDE provide any spectacular differences - only a more Windows like GUI for an easier transition to Linux.


I find [LXDE]("http://lxde.org") to also be a Windows-like GUI but without all the problems getting ordinary applications to work. It also much faster and works better on older hardware than KDE. I suggest LXDE for people who don't like Gnome and don't have the computer resources to run KDE but still prefer a nice "Windowsy"GUI.

-Robin

---

### Post by mntokman on 2009-05-17
> **cariboo907 said:**
> We need more info, before we can help you solve your problems.

[LIST]
[*] Do you get an error message when you insert a music cd?
[*] What is the make and model of your computer?
[*] What wireless chipset does youe wireless device have?
[/LIST]

For a start, go to Start-->Applications-->Utilities-->Terminal and type:

```
lspci
```This command will list your hardware, please paste the output in your next post.

The Output is below and I have a Sony VAIO model# VGN CR220E. Thanks in advance for any help. 

```

mntokman@greenworld:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev61)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
08:07.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:07.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:07.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
mntokman@greenworld:~$



```

---

### Post by smsmith on 2009-06-01
> **mntokman said:**
>  * My wireless network does not work
What is your wireless doing / not doing?

For me, I could connect to my home network, but it would hang on setting the network address.  I pulled my hair out for four hours trying to figure it out and then on a whim changed the WEP security from PASSPHRASE to HEX KEY and it not only connected, but also set a network address.

---

