---
title: "can i install ubuntu to my dell?"
date: 2015-07-08
forum: Desktop Environments
---

### Post by alo12 on 2015-07-08
hellow,

I own a dell t5400. How i will find out if and which version of ubuntu could run to my pc? [http://www.dell.com/support/home/us/en/19/Drivers/SupportedOS/precision-t5400](http://www.dell.com/support/home/us/en/19/Drivers/SupportedOS/precision-t5400)

thank you in advance.

---

### Post by Dennis N on 2015-07-08
I would try booting live version of Ubuntu from a USB installer and see how it runs. That should give you a good indication of how video, audio, network, etc will work.

---

### Post by papibe on 2015-07-08
Hi alo12. Welcome to the forums ):P

Short answer would be yes.

You can test it yourself without installing. Use the installation media, but when you boot into the installer choose 'Try Ubuntu' instead of installing. Once you get to the desktop you can browse the internet, test sound, etc.

The fact the the it says it support 'Red Hat Ent Linux' means that there are good support for the Linux kernel, and thus for most distributions.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by oldfred on 2015-07-09
My Toshiba laptop from late 2006, runs 12.04 64 bit ok, but I have to use fallback which is much lighter weight gui like the old gnome2 with menu. Unity needs a somewhat newer system with more RAM, but really better video card/chip to run well. Unity on laptop was so slow as to be unusable.
Other options are Lubuntu or Xubuntu.

---

### Post by alo12 on 2015-07-09
Can anyone describe me the general differences between ubuntu and lubuntu?

Thank you in advance.

---

### Post by alo12 on 2015-07-09
Thank you all for your help. So the fact that my system support Red Hat Ent Linux is a good "clue". right ? what about lubuntu how different is from ubuntu ?

---

### Post by slickymaster on 2015-07-09
Same repositories, same "core" system, different desktop environments.

Ubuntu comes with the Unity desktop environment. The underlying Unity platform is still GNOME, but instead of using the GNOME Shell interface, Unity uses the Unity shell.

Lubuntu uses the LXDE desktop environment (Lightweight X11 Desktop Environment), which is lighter than Gnome, KDE, and also XFCE. This is ideal for low-memory systems.

---

### Post by coffeecat on 2015-07-09
> **alo12 said:**
> Thank you all for your help. So the fact that my system support Red Hat Ent Linux is a good "clue". right ? what about lubuntu how different is from ubuntu ?

I've merged your two threads so that we don't get the same question asked in more than one, and your question about the differences between Ubuntu and Lubuntu needs to be answered in the context of your hardware.

A 2007 era machine may struggle with the relatively heavy Ubuntu desktop, and Lubuntu may be a better option. However, I suggest you post details of the actual specifications of the machine so that forum members can advise you better.

Ther are also other Ubuntu variants to consider, such as Xubuntu.

---

### Post by grahammechanical on 2015-07-09
Ubuntu uses the Gnome 3 Desktop Environment (DE) with the Unity user interface (UI). Lubuntu is Ubuntu but with the LXDE environment and user interface replacing Gnome 3 (DE) and Unity (UI).

Ubuntu uses Compiz as a window manager/compositor. LXDE uses Openbox as a window manager. It does not have a specific compositor as compositors require more system resources to produce fancy effects which would defeat the purpose of developing LXDE in the first place.

[http://wiki.lxde.org/en/Main_Page](http://wiki.lxde.org/en/Main_Page)

Regards.

---

### Post by oldfred on 2015-07-09
Not only is gui different, but the default applications packaged are different. Defaults usually are also lighter weight versions. But if some application you like is not there, since still Ubuntu repository, you can easily install any other application. If based on a different gui, it may have to install a lot of supporting software.

[http://www.howtogeek.com/163154/linux-users-have-a-choice-8-linux-desktop-environments/](http://www.howtogeek.com/163154/linux-users-have-a-choice-8-linux-desktop-environments/)
[https://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments](https://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments)
       [https://wiki.archlinux.org/index.php/Desktop_Environment](https://wiki.archlinux.org/index.php/Desktop_Environment)

---

### Post by alo12 on 2015-07-09
i have a desktop dell t5400(late 2007) the system is now running microsoft xp sp3) it has "intel xeon cpu E5405 @ 2.00GHZ 2.00GHZ, 3.00BG RAM  physical adress extension" display adapters  NVIDIA QUADRO FX570,NVIDIA QUADRO FX570 .the hard disk is a fujitsu mba 3300rc 300gb 15000rpm

i am thinking of installing the latest [ lubuntu (Intel x86) ]("http://ubuntuforums.org/.") i ahve test it with live cd and it seems to work fine. What do you think? Is this the right choice?

Please let me also know how i can completely clean my hard disk from windows and all the files i have. is it possible through lubuntu instalayion process?

Thank you in advance.

---

### Post by sudodus on 2015-07-09
Lubuntu is a good choice. It is worthwhile to try Xubuntu live too before deciding what to install. You *may* or *may not* prefer speed and responsiveness over a more complete and polished desktop interface. It depends how you will be using the computer too.

Concerning version, I suggest that you select the long time support version, Lubuntu or Xubuntu ***14.04.1*** LTS.

If you want to overwrite Windows, you can simply install Lubuntu or Xubuntu and select to use the whole drive. This will overwrite the file system and Windows.

If you want to be sure that it will not be possible to search for and recover any data from the previous Windows system (for highest security), I suggest that you wipe the drive with ***DBAN*** or ***hdparm***. But in most cases it is not necessary.

---

### Post by alo12 on 2015-07-09
thank you, do you know where i can find i kind of tutorial for wiping my drive with ***DBAN* or [B]*hdparm ?***[/B]

---

### Post by sudodus on 2015-07-10
Wiping with ***hdparm*** is described in [this link](http://ubuntuforums.org/showthread.php?t=2124829&p=12555068#post12555068)

-o-

***DBAN*** is rather self-explanatory - download the iso file flash it to a USB pendrive or burn a CD to boot from and use the basic method, that you can select from the menu.

[http://www.dban.org/download](http://www.dban.org/download)

---

### Post by alo12 on 2015-07-10
thank you one last question please. Should i choose xubuntu or lubuntu iam confused...

---

### Post by coffeecat on 2015-07-10
Why not try them both? You can run the desktop from the live CD/DVD or Live USB without committing yourself to an installation on the hard drive. It will be slower than a proper installation, but it will give you an idea of what the desktop environment is like - Lxde for Lubuntu and Xfce for Xubuntu. Links for Lubuntu and Xubuntu here:

[http://lubuntu.net/](http://lubuntu.net/)

[http://xubuntu.org/](http://xubuntu.org/)

With 3GB of RAM your machine should be OK with the heavier Xubuntu. As far as the choice is concerned, that's mostly down to personal preference - hence the suggestion to try both.

---

### Post by sudodus on 2015-07-10
> **coffeecat said:**
> Why not try them both? You can run the desktop from the live CD/DVD or Live USB without committing yourself to an installation on the hard drive. It will be slower than a proper installation, but it will give you an idea of what the desktop environment is like - Lxde for Lubuntu and Xfce for Xubuntu. Links for Lubuntu and Xubuntu here:

[http://lubuntu.net/](http://lubuntu.net/)

[http://xubuntu.org/](http://xubuntu.org/)

With 3GB of RAM your machine should be OK with the heavier Xubuntu. As far as the choice is concerned, that's mostly down to personal preference - hence the suggestion to try both.

+1 :-)

and I suggest version 14.04.1 LTS.

---

### Post by alo12 on 2015-07-11
should i chooose 32 or 34 bit?

---

### Post by coffeecat on 2015-07-11
According to this, you have a 64-bit processor:

[http://ark.intel.com/products/33079/Intel-Xeon-Processor-E5405-12M-Cache-2_00-GHz-1333-MHz-FSB](http://ark.intel.com/products/33079/Intel-Xeon-Processor-E5405-12M-Cache-2_00-GHz-1333-MHz-FSB)

With 3GB RAM I would suggest you use the 64-bit installer. I presume you mean 64 and not 34. Don't worry that the ISO has AMD64 in the filename. It works with both Intel and AMD 64-bit CPUs. The AMD64 in the filename is there for historical reasons.

---

### Post by alo12 on 2015-07-11
yes i mean 64. Do you think that the 3gb ram and the fact that the computer is 8 eight years old is not a problem for 64bit? 32 bit could also work fine ? i wonder which will fit best...

thank you

---

### Post by sudodus on 2015-07-11
Either follow the advice or try both architectures (32-bit and 64-bit) and make your own judgement :-)

---

### Post by alo12 on 2015-07-11
excuse me xubuntu is something completely new for me and this is the reason why i want to ask so many question. if you thing that 64 bit is the right version you are propably right i just wanted to inform you that my pc is old enough...

---

### Post by sudodus on 2015-07-11
I *think* that ***both Lubuntu and Xubuntu work, and both 32-bit and 64-bit systems work***. If you have a fast and relatively cheap way to download iso files, I suggest that you download several (maybe all four) combinations and try them.

Otherwise, the safest choice (the lightest combination) is Lubuntu 32-bit. But Xubuntu is more complete and polished. And I suggest that you select the version 14.04.1 LTS because it is supported for the longest time, until April 2017. The version 14.04.2 LTS might be more convenient (need less updating after the installation), but the kernel in not updated for the same long period.

This link contains links to all Ubuntu flavours: [http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by alo12 on 2015-07-12
you are right i have test both xubuntu and lubuntu versions. thexubuntu 64 bit works fine.

---

### Post by sudodus on 2015-07-12
Great :KS

When you feel that your original problem of this thread is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

If you run into other problems or want other tips about software, please start a new thread with a good descriptive title in order to attract people who are interested and know about that subject.

---

