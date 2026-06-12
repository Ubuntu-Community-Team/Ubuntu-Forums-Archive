---
title: "Buying help"
date: 2007-12-10
forum: Dell  Ubuntu Support
---

### Post by HuBaghdadi on 2007-12-10
Hi.
I'm going to buy "DELL Inspiron 1520" laptop.
Do you advice me to proceed?
I'm going to install Ubuntu 7.10
Thank you.

---

### Post by linux23dragon on 2007-12-10
> **HuBaghdadi said:**
> Hi.
I'm going to buy "DELL Inspiron 1520" laptop.
Do you advice me to proceed?
I'm going to install Ubuntu 7.10
Thank you.


The Web cam is good.
Nvidia is good (and so is ATI but Nvidia is best)
Intel HDA Sound card support works and is getting better driver support.
Intel Pro/Wireless 3945ABG works better with Ubuntu-7.10 than it did with Ubuntu-7.04 (And driver support should improve as time goes on).
The default Bluetooth works fine.
USB works
Firewire IEEE1394 works
DVD +/- Burner works well too.
Digital Microphone works well.
Ethernet is also good.


Yep,  The 1520 is starting to shape up.  There is very little to configure with Ubuntu-7.10 but you will need to follow some good tips.

[***_[COLOR="Blue"]Intel HDA (Sound support)[/COLOR]_***]("http://ubuntuforums.org/showthread.php?t=635274&highlight=dell+1520&showpost=#9")
[***_[COLOR="Blue"]How To Install Ubuntu 7.10 (Gutsy) on Dell Inspiron 1520[/COLOR]_***]("http://ubuntuforums.org/showthread.php?t=577469&highlight=dell+1520")

And if you encounter any funny issues with Ubuntu, you can search this forum with key words like "bluetooth gutsy", "bluez gutsy" and "libdvdcss2 gutsy" (without the quotes).

Hope this helps.

Oh and you should be able to play DVD s  after you install libdvdcss2 like this.

Paste this command into the terminal to install libdvdcss2 : -
```

sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by HuBaghdadi on 2007-12-10
Well, this laptop is supposed to run Intel Core 2 Duo
Which version of Ubuntu should I get?
32 bit version or 64 bit version?

---

### Post by linux23dragon on 2007-12-10
> **HuBaghdadi said:**
> Well, this laptop is supposed to run Intel Core 2 Duo
Which version of Ubuntu should I get?
32 bit version or 64 bit version?

I've tried both the 32bit and 64bit versions when they were first released in October.

Ubuntu-7.10 64bit installs fine and works fine, but can be harder to set up correctly with the Inspiron 1520.  The problems (with 64bit) that occurs is with the boot splash, and "may be" some device driver setups. 

You can find lots of information to get everything running correctly reading the threads in the Ubuntu forums.   The Ubuntu updates could also have fixed all of the issues already, but be prepared.   


Ubuntu-7.10 32bit has no such troubles (compared to the 64bit), and should just work.


You can try out both 32bit and 64bit  to see that for yourself..

---

### Post by natehall on 2007-12-10
> **HuBaghdadi said:**
> Well, this laptop is supposed to run Intel Core 2 Duo
Which version of Ubuntu should I get?
32 bit version or 64 bit version?

The preinstalled Ubuntu on the 1420N uses 32 bit Ubuntu even though the chip is 64 bit. Dell does this because some drivers are not supported in 64 bit yet.

---

### Post by notwen on 2007-12-11
I purchased a Inspiron 1420n and am very pleased w/ it.  The 1520 is said to be fairly compatible for the most part w/ some minor tweaks.  If you don't mind tinkering every so often to perfect your machine, I'd highly recommend supporting Dell's decision to offering Dell-buntus by purchasing one of your own.  Good luck w/ whatever you decide. =]

---

### Post by bluedragon436 on 2007-12-11
I think for most people running the 32bit version is the best bet, I mean I have been running it on my 64bit desktop and have had no issues, and I have tried to install the 64bit, and didn't even see a difference other than more of a PITA to set up....  I have thought about purchasing the 1520 as my next laptop, but may end up going with the 1420n pre-loaded from Dell...

---

