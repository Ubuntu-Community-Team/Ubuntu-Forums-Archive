---
title: "how can i mount .iso games in ubuntu"
date: 2013-06-23
forum: Gaming &amp; Leisure
---

### Post by AbhimanyuAryan on 2013-06-23
i was playing gta4, assasin's creed 3 and few other games on my laptop running windows 7 untill i completely switched over to ubuntu.....is there any way that i can mount .iso files like windows run the setup?.........install>play

i have wine but it works with .exe not .iso........so i would love to hear if there's any software like daemon tool in ubuntu with which i can mount .isos:):):)

---

### Post by efflandt on 2013-06-23
First you need to create a mount point (mkdir, which if in a path like /media/something you would need to use sudo mkdir). Then you loop mount the iso file:

```
sudo mount -t iso9660 /path_to/some.iso /some_directory -o loop
```where **/path_to/some.iso** would be the full or relative path to the iso file and **/some_directory** is the mount point you created to mount it on. Then you can **cd** to that directory you mounted it on(or go to it with a file manager) and could see setup.exe or whatever.

But I have never used wine, so I am not sure where you would want to mount it to have it accessible to wine. I just run Linux specific games, Linux Steam games, or OS independent java games like minecraft.

---

### Post by xREDEMPTIONx on 2013-06-23
I suggest acetoneISO. Search for it in the software center. You can also run 'sudo apt-get install acetoneiso' in a terminal to install it. Makes mounting and unmounting iso's a breeze. After you install it just right click an iso file, select "properties", then "open with", then select acetoneISO from the list and set is as default. Then in the future when you want to mount an iso just left click on it and it will acetoneISO will automatically start and mount your image:)

---

### Post by oldrocker99 on 2013-06-23
What he said. AcetoneISO is the open-source version of the extremely wildly pirated Alcohol120% Windows program, which does the same thing for $$$, or is usually infected with malware. Reason #98947224542 for dumping Windows in favor of GNU/Linux.

---

### Post by Lightning Dragon on 2013-06-24
Hi,

I would suggest GMount-ISO. It is easy to use and even has an "unmount" button with it. You can install this via the terminal or the Software Center. Here is a link with instructions on how to use GMount-ISO.

[http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html](http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html)

Good luck!

---

### Post by ushpiy on 2013-06-26
Like others said try AcetoneISO I have used it before and its okay.

---

### Post by varunendra on 2013-06-26
> **AbhimanyuAryan said:**
> i have wine but it works with .exe not .iso........so i would love to hear if there's any software like daemon tool in ubuntu with which i can mount .isos:):):)

Take a look at [CDEmu]("http://cdemu.sourceforge.net/about/") project. So far this is the only program I've found that is really close to DaemonTools in windows. The only program to actually emulate a physical optical drive, and also supports a lot of image formats like daemontools.

I have used (and keep using for various reasons) AcetoneISO, Gmount-ISO and many more, but all they do is to mount the iso so you can access the contents. The OS does not recognize these mounted images as "physical CDs". Only the images mounted on CDEmu drives were actually recognized as physical CDs.

For games, I have personally tested it successfully with a very old cd-based game "StarWars - Rogue Squadron". Its installer running in wine detected the iso as a cd only when mounted with cdemu, not with AcetoneISO or any other method, including the commandline way and some tweaking to make it appear as a physical cd.

PPA for installing CDEmu on Ubuntu : [https://launchpad.net/~cdemu/+archive/ppa](https://launchpad.net/~cdemu/+archive/ppa)

---

### Post by oldrocker99 on 2013-06-28
Verrrry interesting. I'd not heard of CDEmu, but I'm heading there now.

Boy, this is simply the best farking forum anywhere.

---

### Post by dannyboy79 on 2013-06-28
you'll need to see if those games work in wine otherwise theres no point in trying to mount an iso of a windows game

---

