---
title: "ePSXe trouble with Karmic"
date: 2009-10-25
forum: Gaming &amp; Leisure
---

### Post by tomek.vz on 2009-10-25
Hello everyone.

I have been using Ubuntu 9.10 x86_64 for a week now and al works perfect exept one thing - ePSXe. When i run it i get:

```

tomek@TRITON:~/Programi/Ostalo/Igre/PSX/ePSXe$ ./epsxe 
Killed
```I don't know how to get something usefull to tell me what's wrong so i would appreciate if u could help me. I think that the problem lies in dependencies which are missing from karmic:

[ePSXe Linux HOWTO]("http://forums.ngemu.com/generic-epsxe-queries/93374-epsxe-configuration-guide-linux.html")

> **Install dependencies:**
Make sure that you have the latest updates for your linux distribution, as many required dependencies will already be installed.
Open terminal and input the following commands:
```
sudo apt-get install unzip libgtk1.2-common libgtk1.2 libsdl-net1.2-dev libsdl-image1.2-dev libsdl1.2-dev
sudo apt-get install libstdc++2.10-glibc2.2
```Any ideas?

---

### Post by Alibbi on 2009-10-25
I'm interested in this, too.
The problem is related to the Karmic development versions, maybe the cause is that epsxe requires **libtgtk1.2** instead of **libgtk2** (default). But even a manual installation fails to solve the problem.
I tied also a chmod 777, with no results.

Others emulators like pSX and PCSX-df are **not** at the same level. ](*,)

---

### Post by DoktorSeven on 2009-10-25
Well, if you are running 32bit you can easily grab the GTK1.2 libraries from its website ( [http://ftp.gnome.org/pub/gnome/sources/gtk+/1.2/](http://ftp.gnome.org/pub/gnome/sources/gtk+/1.2/) ).  Extract, ./configure --prefix=/usr then make then sudo make install should install it.

However, 64bit isn't as easy since ePSXe is a 32bit program and it depends on 32bit libraries... and compiling GTK1.2 will get you a 64bit GTK1.2 library... :(

---

### Post by tomek.vz on 2009-10-26
Guys...solved it:

```
sudo apt-get install upx-ucl
cd /your_epsxe_dir
upx -d epsxe
```

---

### Post by DoktorSeven on 2009-10-26
That helps if you only have the problem of ePSXe not running but have the required libs installed.  My problem was getting the proper GTK 1.2 libraries in a 64-bit system.

I solved it by downloading [the Jaunty 32-bit version of libglib1.2](http://packages.ubuntu.com/jaunty/libglib1.2ldbl) and [the Jaunty 32-bit version of libgtk1.2](http://packages.ubuntu.com/jaunty/libgtk1.2).  Download and save them, do not run them with an installer.  (Yes, the Jaunty version, even though this is Karmic.  Karmic doesn't have libgtk1.2 libraries available anymore.  This is very unsupported, of course, and the risk is yours although I haven't had any problems with it.)

Place them in a temporary directory somewhere, open a command prompt, cd to the directory and type

**dpkg -x libglib1.2ldbl_1.2.10-19build1_i386.deb .**
**dpkg -x libgtk1.2_1.2.10-18.1build2_i386.deb .**

Note the dot at the very end, this means "extract here".  **cd usr/lib** (not /usr/lib, the usr/lib directory under the current one that dpkg just created) and copy all the libraries and symbolic links to /usr/lib32 (*make sure you don't copy them to /usr/lib or /usr/lib64*:

**sudo cp * /usr/lib32**

Ran fine after that; if you do still get an error you might need to download and run upx as shown above.

---

### Post by Alibbi on 2009-10-27
Very well done, my companions! :D

---

### Post by Thehound on 2009-10-31
To my surprise pcsx-df works better than epsxe ever did for many games with the same plugins. This emulator also works fine without the hackish install. It used to be way behind epsxe, but that's in the past now. I was cursing Karmic for the epsxe issues, but realize it actually did me a favor by letting me discover something better.

---

### Post by comsparks on 2009-11-02
I'm trying to install XMMS old version. I had it running in 9.04 but have issues with libgtk1.2 (>=1.2.10-4). I did what you said above and put it in lib32 folder but nothing. I was just checking if you know how to get this up and running using that libgtk1.2. I've checked everything on the internet and forums and at wits end. Thanks

---

### Post by comsparks on 2009-11-02
I'm running Karmic 9.10 now.

---

### Post by DoktorSeven on 2009-11-02
> **comsparks said:**
> I'm trying to install XMMS old version. I had it running in 9.04 but have issues with libgtk1.2 (>=1.2.10-4). I did what you said above and put it in lib32 folder but nothing. I was just checking if you know how to get this up and running using that libgtk1.2. I've checked everything on the internet and forums and at wits end. Thanks
If XMMS doesn't compile in 64-bit you'd need 32-bit packages of at least XMMS, libgtk1.2 and libglib1.2, plus anything else XMMS depends on.

Theoretically the best answer would be to compile everything for 64bit, but I'm not sure they'd all compile cleanly or not (they're old packages).

**Update:**  Compiling it works in 64bit, but you will need to patch both glib1.2 and gtk1.2 using the "diff" files found on the Ubuntu package pages I linked in my earlier post (on the right side of the page, the files ending in "diff.gz").  Otherwise it gives you problems trying to configure and compile these in 64bit.  

I wrote up a little rough howto [here](http://doktorseven.miskie.net/page.php?6), it worked for me :)

---

### Post by comsparks on 2009-11-02
I have a 32bit configuration.

---

### Post by DoktorSeven on 2009-11-02
> **comsparks said:**
> I have a 32bit configuration.

Then you should just be able to compile them from source or use the existing Jaunty packages, but you have to make sure to install both gtk+1.2 and glib1.2, their -dev packages, and -dev packages of OSS and/or ALSA, mikmod, and Ogg Vorbis to compile XMMS.

See my writeup about supporting FLAC; should be similar for 32-bit, you'd just put it in /usr/lib/xmms/Plugins.

---

### Post by comsparks on 2009-11-02
Thanks. I'm trying to figure out all of what you have said. You are way ahead of me with your knowledge about Linux. As soon as I get my eyes uncrossed and brain clear I'll try to put this together. It looks like a very complicated process.

---

### Post by maxadocious on 2009-11-06
I tried the first fix w/ upx, and that seemed to do something, but I'm getting this error msg now, and I'm wondering if I need to do the second part w/ libgtk-1.2 I'm just curious if there's any way that this could seriously damage my computer. I finally got Karmic working well for myself, and I would hate to have to wipe it again.

Here's the error.

./epsxe error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

thx, you guys rule

---

### Post by tomek.vz on 2009-11-06
> **maxadocious said:**
> I tried the first fix w/ upx, and that seemed to do something, but I'm getting this error msg now, and I'm wondering if I need to do the second part w/ libgtk-1.2 I'm just curious if there's any way that this could seriously damage my computer. I finally got Karmic working well for myself, and I would hate to have to wipe it again.

Here's the error.

./epsxe error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

thx, you guys rule

You need to install 32bit libgtk1.2 (i just extract files and then copy files from lin dir into /usr/lib32)...search for it at [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by Dark Aspect on 2009-11-06
[Take the easy way out]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=12203")

---

### Post by naldin on 2009-11-14
I have the same problem. There is any problem in the install this libs? The libs 2.0 continued working?

> **DoktorSeven said:**
> Well, if you are running 32bit you can easily grab the GTK1.2 libraries from its website ( [http://ftp.gnome.org/pub/gnome/sources/gtk+/1.2/](http://ftp.gnome.org/pub/gnome/sources/gtk+/1.2/) ).  Extract, ./configure --prefix=/usr then make then sudo make install should install it.

However, 64bit isn't as easy since ePSXe is a 32bit program and it depends on 32bit libraries... and compiling GTK1.2 will get you a 64bit GTK1.2 library... :(

---

### Post by Ioky on 2009-11-15
Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directoryioky

I am getting this error, when I try to configure anything release to plugins like when I click on video. or sound.

am trying to solve it, not sure how at the moment. haha

---

### Post by Ioky on 2009-11-15
Please forget my dumb-ness I solved, and it is actually one of my old post, tell people who to solve this. 

however, the Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory

is still there, anyone have any idea? although it doesn't seem effecting anything.
PS: running epsxe with sudo do solve the problem. but you might now what that. the libcanberra-gtk-module is already there in /usr/lib32/gtk2.0/module. so it might be a permission issue too, But I am not sure I should change the permission

--.--!! haha anyway 

Here is the [Link]("http://ubuntuforums.org/showthread.php?t=1027044&highlight=epsxe+64bit+ubuntu")

good lucky

---

