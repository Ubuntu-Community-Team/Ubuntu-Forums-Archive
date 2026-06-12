---
title: "Ubuntu GUI Flexibility."
date: 2007-07-10
forum: Desktop Environments
---

### Post by LinuxNathan on 2007-07-10
Hello. I used to be a big fan of Windows 2000 PRO until I ran into Mandriva linux. Though now I am back at Windows 2000 PRO, and my unbuntu loving friend directed me to unbuntu if i ever wanted to get back into linux.

Well, here I am. I was wondering. About how flexible is it's GUI, and could you make it look like the Mandriva KDE? Also if it had a built in C or Native C++ Win32/API compiler?

Thanks! :)

PS: C compiler is good enough. :)

---

### Post by spoilerhead on 2007-07-10
just install KDE (look for "kubuntu-desktop" in synaptic)

c compiler: gcc (installing "build-essentials" should give you a basic setup)
win32 api, not really. winelib can do some tricks, but better get used to gcc first

---

### Post by jespdj on 2007-07-10
Ubuntu comes with the GNOME desktop.

If you want KDE, then you can install the package kubuntu-desktop and from the login screen choose a different session, and choose KDE.

If you don't want to use the GNOME desktop at all and you want only KDE, then it's a good idea to use Kubuntu: [http://kubuntu.org/](http://kubuntu.org/) - This is exactly the same as Ubuntu, but with KDE as the default desktop instead of GNOME.

The C and C++ compiler that you get with almost any kind of Linux is GCC. GCC version 4.1.2 is installed with (K)ubuntu 7.04, but before you start compiling your own programs you need to install an extra package with the standard C/C++ library header files:
```
sudo apt-get install build-essentials
```

If you want to program for Linux, then forget about Win32...

There are several GUI programming toolkits available; for GNOME the standard GUI toolkit is GTK+, for KDE it is Qt.

---

### Post by RedSquirrel on 2007-07-10
The package is **build-essential**.

```
sudo apt-get install build-essential
```

---

### Post by LinuxNathan on 2007-07-10
Thanks guys! Well, I reckon i should download ubuntu (Not kubuntu (that just looked plain wierd (Roflz))) and try it for myself!

Thanks again for the help! :)

---

### Post by RedSquirrel on 2007-07-11
I believe you can also build up a custom KDE rather than using Kubuntu. There are packages related to KDE in the repositories that you can install individually rather than installing kubuntu-desktop. I don't know exactly what they are named because I use Fluxbox, but it might be worthwhile to do some searches on the forums and the web and in Synaptic to see what you can come up with.

You might be just as happy with the regular Ubuntu and GNOME, but if the time comes that you want to use KDE without Kubuntu, you could investigate a little. ;)

Good luck.

---

### Post by stchman on 2007-07-11
> **LinuxNathan said:**
> Hello. I used to be a big fan of Windows 2000 PRO until I ran into Mandriva linux. Though now I am back at Windows 2000 PRO, and my unbuntu loving friend directed me to unbuntu if i ever wanted to get back into linux.

Well, here I am. I was wondering. About how flexible is it's GUI, and could you make it look like the Mandriva KDE? Also if it had a built in C or Native C++ Win32/API compiler?

Thanks! :)

PS: C compiler is good enough. :)



The build-essential I believe does not contain any M$ headers.  I have found programming the Windows interface a pain.  That is what VB, Java, and Python are for.

---

