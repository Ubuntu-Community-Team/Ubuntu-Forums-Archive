---
title: "pcsx troubles"
date: 2007-12-15
forum: Gaming &amp; Leisure
---

### Post by yipeskop on 2007-12-15
I installed pcsx from synaptic and started it up, but when I told it to open a .bin file it just shut itself off without any error message.
any help plz?

---

### Post by FranMichaels on 2007-12-15
Have you gone through the Configuration menu?

Go through the menu, make sure every option is set (except netplay, that's optional.)

Here is a screenshot of my settings (ctrl + p).

Press ctrl + m (or pick it from the Configuration menu) to create virtual memory cards.

---

### Post by yipeskop on 2007-12-15
yes, it is all configured right but still wont work.

---

### Post by acoustibop on 2007-12-15
What .bin file are you trying to open, yipeskop?

TBH PCSX is pretty long in the tooth now and complicated to configure so it runs properly.  I'd recommend [pSX Emulator]("http://psxemulator.gazaxian.com/") - it's the only Linux Playstation emulator still in development and is much easier to install and configure than PCSX or [ePSXe]("http://www.epsxe.com/").

---

### Post by yipeskop on 2007-12-15
I tried installing pSX emulator before but, I always get the folowing error when installing it:

./psx: error while loading shared libraries: libgtkglext-x11-1.0.so.0: cannot open shared object file: No such file or directory

Thats why I just used pcsx. (but if you knew how to fix the stated error above to get pSX emu to work that'd be awesome ^^)

---

### Post by FranMichaels on 2007-12-15
> **yipeskop said:**
> 
./psx: error while loading shared libraries: libgtkglext-x11-1.0.so.0: cannot open shared object file: No such file or directory


Try this :)

```
sudo apt-get install libgtkglext1
```

---

### Post by yipeskop on 2007-12-15
nope, still the same error :(

---

### Post by FranMichaels on 2007-12-15
> **yipeskop said:**
> nope, still the same error :(

Oops. :)

```
sudo apt-get install libgtkglext1-dev
```

Sorry, I thought that library would be in the regular package, not the dev one :)

---

### Post by yipeskop on 2007-12-15
it installed 37 new things but still the same error :(

---

### Post by FranMichaels on 2007-12-15
```
locate libgtkglext-x11-1.0.so.0
```

This should show some results:

/usr/lib/libgtkglext-x11-1.0.so.0.0.0
/usr/lib/libgtkglext-x11-1.0.so.0

If the files do exist and pSX can't see it.

```
sudo ldconfig
```

If that doesn't do it, I'm out of ideas :KS

---

### Post by yipeskop on 2007-12-15
> **FranMichaels said:**
> ```
locate libgtkglext-x11-1.0.so.0
```

This should show some results:

/usr/lib/libgtkglext-x11-1.0.so.0.0.0
/usr/lib/libgtkglext-x11-1.0.so.0

If the files do exist and pSX can't see it.

```
sudo ldconfig
```
files
If that doesn't do it, I'm out of ideas :KS

I did the code no results of any kind were shown (errors or the files you mentioned). I looked in the /usr/lib/ directory and found the file "libgtk2.0-0" and "gtkglext1.0" but no libgtkglext though. (I also found this in the lib32 and lib64 directories.)

---

### Post by acoustibop on 2007-12-16
Open Synaptic and search for libgtkglext1, yipeskop.  It's in the Universe repository, which you should have enabled by default.

If it isn't there, something's very wrong.

---

### Post by dfreer on 2007-12-16
Sounds like the OP is running a 64-bit OS to me... is this the case? The files pSX are complaining about are part of the [libgtkglext1]("http://packages.ubuntu.com/gutsy/libs/libgtkglext1") package, which as been said is in the universe repos. On a 32-bit install, it should be as simple as downloading the .deb and installing it.

On a 64-bit install, you'll need to download the **32-bit** libraries and install them as the 64-bit libraries won't work with pSX (pSX is a 32-bit binary and can only use 32-bit shared libaries). You can either do this manually, or you can download lib32gtkglext1 from my site (pSX as well if you wish).

---

### Post by yipeskop on 2007-12-16
> **dfreer said:**
> Sounds like the OP is running a 64-bit OS to me... is this the case? The files pSX are complaining about are part of the [libgtkglext1]("http://packages.ubuntu.com/gutsy/libs/libgtkglext1") package, which as been said is in the universe repos. On a 32-bit install, it should be as simple as downloading the .deb and installing it.

On a 64-bit install, you'll need to download the **32-bit** libraries and install them as the 64-bit libraries won't work with pSX (pSX is a 32-bit binary and can only use 32-bit shared libaries). You can either do this manually, or you can download a lib32gtkglext1 from my site (pSX as well if you wish).

Ya I am using a 64 bit OS (guess I should have mentioned that sry >_<) and when I do the code on your guide:

```
wget http://packages.dfreer.org/7572013D.gpg -O- | sudo apt-key add -
``` 
but I keep getting the error

```
Resolving packages.dfreer.org... 209.173.166.154
Connecting to packages.dfreer.org|209.173.166.154|:80... 
failed: Connection timed out.
 
```

edit: after going to  /etc/apt/sources.list and removing "http://packages.dfreer.org" and trying again, it installed pefectly and pSX played my image just fine thx a lot for all of your help ^^

---

### Post by dfreer on 2007-12-16
Sorry about the site error yipeskop... lots of things going on around here and the site was down temporarily :(
Anyways, glad everything is working for you now though!

---

