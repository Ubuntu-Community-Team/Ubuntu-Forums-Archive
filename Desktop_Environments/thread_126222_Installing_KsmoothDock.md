---
title: "Installing KsmoothDock"
date: 2006-02-06
forum: Desktop Environments
---

### Post by ThirdGenLS1 on 2006-02-06
I'm still new to linux, and have had Ubuntu on my machine for almost a month(completly deleted windows and installed ubuntu).  Before installing it i have never used or seen linux but figured i'd give it a try.  Any ways i've come a long ways in the last month but i still dont completly understand how to install apps.  I've downloaded ksmoothdock from kde-apps.org and i'm wondering how to install it.

Thanks a lot 
Justin

---

### Post by Jucato on 2006-02-06
Which version/type did you download? There different ways to install an application/program depending on what type of installer was downloaded. 

1. The easiest: through Adept/apt-get/etc: through the repositories. Just pick out the package you need and install. Everything is automated. All dependencies are checked, downloaded, and resolved (if possible)

2. Moderately easy: DEB packages. If you download a package of .deb type, you type this in the console:
```
$ sudo dpkg -i *package name.deb*
```
or you could right-click the .deb file and choose the proper action from Konqueror (if you are running Breezy). Take note that this method does not download any dependencies. It only checks whether you are missing some of them. you have to download and install these yourself.

3. Moderately difficult: Compiling and Installing from Source Code. Some people, the more advanced ones, prefer to use this method instead of downloading .deb files, because compiling straight from source code customizes the application to your particular system/configuration. I'm not an expert in this method myself, so I can only share with you the basic steps:

1. Untar (or unzip) the package you downloaded. They usually come in .tar.gz or .tar.bz2
2. Go to the untarred/unzipped directory
3. type these (you have to wait for each process to finish before typing the next command)
```
./configure
make
sudo make install
```
The reason this method is not so easy is because there are many things to consider here. Like I said, I'm not an expert in this part.

Back to the main topic: I see that KSmoothDock comes in different packages:
1. Version 3.6.1 and 3.5.1 source codes
2. Version 3.5.1 Debian SID (this is a .deb file)
3. Version 3.5.1 SuSE 9.1 (an .rpm)

I suggest you download and install the Debian SID version, unless you plan to learn and experiment on compiling source code yourself.

---

### Post by ThirdGenLS1 on 2006-02-06
i downloaded version 3.6.1 its a tar.gz file.

---

### Post by ThirdGenLS1 on 2006-02-06
i figured it out thx

---

### Post by hustle7 on 2007-03-22
> **ThirdGenLS1 said:**
> i figured it out thx

Hi. I'm trying to download ksmoothdock 4.3. Could you tell me how installed ksmoothdock?

---

### Post by MontanaMax on 2007-04-03
There is a howto guide for version 4.3 here

[https://help.ubuntu.com/community/KSmoothDock](https://help.ubuntu.com/community/KSmoothDock)

Please let me know how it works in case there is something I need to add to it.

Good luck!

---

### Post by TheCleaner on 2007-04-03
> **MontanaMax said:**
> There is a howto guide for version 4.3 here

[https://help.ubuntu.com/community/KSmoothDock](https://help.ubuntu.com/community/KSmoothDock)

Please let me know how it works in case there is something I need to add to it.

Good luck!


I followed that article and got it installed but when I launch it it says "The application crashed and caused the signal (8)"

```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
KCrash: Application 'ksmoothdock' crashing...
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

---

### Post by MontanaMax on 2007-05-14
With that stream of error messages, I think you might have some configuration entries for devices in your xorg.conf file that aren't working completely (such as Wacom Tablet entries that don't work all the way) or video / monitor entries that aren't completely smooth.

This is getting a little over my head, and while I'm happy to try to help figure it out you might end up with better results leaving a comment on the kde-apps.com ksmoothdock discussion page where the primary developer keeps an eye on things.

If that doesn't work, or you don't spot anything obviously out of sorts, please post your xorg.conf file and we'll all take a crack at finding the issue. :)

Good luck!

---

### Post by Pitot on 2007-05-26
hello there, I just installed ubuntu in my computer and I find it to be a great way to start with Linux. The beryl cube is great! and Im trying to install the ksmoothdock but was not successful. I unpacked the package and tried to compile it but was getting 1 error:

Making install in autom4te.cache
make[1]: Entering directory `/opt/ksmoothdock-4.3_automake1.9/autom4te.cache'
make[1]: *** No rule to make target `install'.  Stop.
make[1]: Leaving directory `/opt/ksmoothdock-4.3_automake1.9/autom4te.cache'
make: *** [install-recursive] Error 1

and when I run the application I get this as backtrace:

Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
[Thread debugging using libthread_db enabled]
[New Thread -1232156976 (LWP 18325)]
[KCrash handler]
#6  0x0806904b in IconBasedDockItem::generateIcons ()
#7  0x0806948c in IconBasedDockItem::IconBasedDockItem ()
#8  0x08068a75 in DesktopSelector::DesktopSelector ()
#9  0x08056f99 in KSmoothDock::initPager ()
#10 0x08059341 in KSmoothDock::KSmoothDock ()
#11 0x08053440 in main ()

I appriciate your time in taking a look at this and I really want to learn how to make it work. thanks a lot!! :)

---

### Post by MontanaMax on 2007-05-26
I'm not sure if ksmoothdock works with Beryl/Compiz or not - I haven't been able to get Beryl/Compiz working on my system at all to try. 

I'd suggest asking the primary developer (Dang) over at [http://www.kde-apps.org/content/show.php?content=6585](http://www.kde-apps.org/content/show.php?content=6585) - he's very responsive and helpful.

Good luck!

---

