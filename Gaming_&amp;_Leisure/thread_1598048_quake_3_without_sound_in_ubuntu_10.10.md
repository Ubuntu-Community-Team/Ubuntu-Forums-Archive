---
title: "quake 3 without sound in ubuntu 10.10"
date: 2010-10-16
forum: Gaming &amp; Leisure
---

### Post by jcer93705 on 2010-10-16
Hi i've gotten to work while back with fedora and older version of ubuntu with the command that we use for wolf. Now since i have ubuntu 10.10 i cant get it to work. Any idea guys?



------- sound initialization -------
/dev/dsp: No such file or directory
Could not open /dev/dsp
------------------------------------
Sound memory manager started
Loading vm file vm/ui.qvm.
VM file ui compiled to 594408 bytes of code
ui loaded in 1963008 bytes on the hunk
Can't use keys or values with a "
107 arenas parsed
39 bots parsed
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: jaime-Satellite-L505D
Alias: localhost6.localdomain6
Alias: localhost6
IP: 192.168.2.2
IP: 127.0.0.1
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
^5PunkBuster Client: PunkBuster Client (v0.993 | A0) **DISABLED**
^3PunkBuster Server: PunkBuster Server (v0.993 | A0 C0.0) **DISABLED**
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console

---

### Post by alexandrius on 2010-10-16
did you try padsp?

---

### Post by jcer93705 on 2010-10-16
> **alexandrius said:**
> did you try padsp?

------- sound initialization -------
Sorry but your soundcard can't do this


It's a no go.

---

### Post by jcer93705 on 2010-10-24
Help!!!!!!!!!!!!!!!!!1

---

### Post by tcrapper on 2010-10-25
If you want /dev/dsp back you have to compile your own kernel, ubuntu developers decided the majority of people don't need OSS support.

[http://vanvalkinburgh.org/blog/3153](http://vanvalkinburgh.org/blog/3153)

---

### Post by jcer93705 on 2010-10-25
> **tcrapper said:**
> If you want /dev/dsp back you have to compile your own kernel, ubuntu developers decided the majority of people don't need OSS support.

[http://vanvalkinburgh.org/blog/3153](http://vanvalkinburgh.org/blog/3153)

Do i just install it as normally when its a deb? Or theres more to it?

---

### Post by tcrapper on 2010-10-25
> **jcer93705 said:**
> Do i just install it as normally when its a deb? Or theres more to it?

yeah just double click it. you need the headers file too. after you install it reboot, you should go in the new kernel, you can see what kernel your using by typing uname -a.

---

### Post by jcer93705 on 2010-10-25
> **tcrapper said:**
> yeah just double click it. you need the headers file too. after you install it reboot, you should go in the new kernel, you can see what kernel your using by typing uname -a.

Wireless didn't work. I'm getting tired of this gaming thing in linux.

---

### Post by tcrapper on 2010-10-25
> **jcer93705 said:**
> Wireless didn't work. I'm getting tired of this gaming thing in linux.

so your wireless works with the default kernel? you can get back to the other kernel by holding shift while it boots up.

---

### Post by jcer93705 on 2010-10-25
> **tcrapper said:**
> so your wireless works with the default kernel? you can get back to the other kernel by holding shift while it boots up.

Actually my grub let me select which kernel to run. No biggie that part. People that work on kernel should not leave behind old technology because theres some people using it.

---

### Post by pall.q3 on 2010-10-29
Hi to all.
Same situation here - cant find this dir.
Is any other way then installing custom kernel?
May be we can give to q3 some command to look for different dir that we can create?

---

### Post by Rhemat on 2010-11-16
I'm trying to figure this out as well, and getting really annoyed.  I have a thread here:

[http://ubuntuforums.org/showthread.php?t=1622208](http://ubuntuforums.org/showthread.php?t=1622208)

However, I've made absolutely no progress what-so-ever.

JCER, what wireless NIC do you have?  I want to try that kernel, but something tells me that I won't have much more luck.

---

### Post by feci on 2011-03-28
Hello all,

this thread is quite old, but still if you haven't found a solution for running quake3 on ubuntu 10.10 (meerkat) and perhaps older / other versions of linux, you could the script from:
[http://nullkey.kapsi.fi/et-sdl-sound/](http://nullkey.kapsi.fi/et-sdl-sound/)

I've also tried a lot stuff to sort out the OSS problem, including all the previously mentioned workarounds but neither of them worked for me, except the script from link above :-)
Hope it helps.

---

