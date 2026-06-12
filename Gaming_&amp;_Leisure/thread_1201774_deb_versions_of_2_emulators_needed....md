---
title: "deb versions of 2 emulators needed..."
date: 2009-07-01
forum: Gaming &amp; Leisure
---

### Post by dcninja on 2009-07-01
can someone post up a deb version of a tg16 (pcengine) emulator and a sega master system emulator for ubuntu? I'd like the gui versions of the emulators please. Supposedly XE will emulate both of these but I can't find a deb. I hear hugo is good for tg16 but i dunno if it has a gui. Meka works for sega master system from what I've seen, but no deb. Thanks for the help in advance.

---

### Post by Nevon on 2009-07-01
Can't Gens/GS handle Sega Master System?

---

### Post by farrell2k on 2009-07-01
XE will handle everything you need.   I just moved back to ubuntu from debian and I am in the process of setting up my system.   I will be happy to post an x86 binary when I am finished, if the forums allow this.

---

### Post by dcninja on 2009-07-01
no gens doesn't do sms in linux... I know xe handles turbografx and master system but I can't find a deb to install the thing! if anyone can link up to one that'd be great! It's the only thing keeping me from fully switching to pure linux! :)

---

### Post by dcninja on 2009-07-01
you think you'll have it up today? i'm going on vacation tomorrow and I won't have internet access for a while, trying to finish setting things up on my lil netbook so i have stuff to play.

---

### Post by Grishka on 2009-07-01
[this](apt://mednafen) is all you need.

edit: ah, you wanted something with a gui, mednafen doesn't have one. but press F1 in-game to see how to configure stuff.

---

### Post by dcninja on 2009-07-01
i was hoping to find a deb of the XE emulator... anyone?

---

### Post by Nevon on 2009-07-01
Why do you need a package? Just download the Linux tarball, cd into it and type:

sudo make
sudo make install

---

### Post by Grishka on 2009-07-01
> **Nevon said:**
> Why do you need a package? Just download the Linux tarball, cd into it and type:

sudo make
sudo make install

hey, never make as root.

```

make
sudo make install

```

is the way to go.

---

### Post by dcninja on 2009-07-01
tried it, here's result
cninja@dcninja-netbook:~$ cd xe-x86
dcninja@dcninja-netbook:~/xe-x86$ dir
install.sh  libxe.a  Makefile  manual.html  modules  rc  README.txt
dcninja@dcninja-netbook:~/xe-x86$ make
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
/usr/bin/ld: cannot find -lasound
collect2: ld returned 1 exit status
make: *** [xe] Error 1
dcninja@dcninja-netbook:~/xe-x86$

---

### Post by Col-1023 on 2009-07-01
I've never compiled anything, but I believe you have to have the package called build-essentials installs before you compile sources.

I've also read that the command checkinstall will create a deb.

There should be a wiki somewhere on compiling.

Hope this helps.

---

### Post by dcninja on 2009-07-01
im sort of a noob to linux, right now id like to get it up and running before i fiddle with stuff like that, i tried what you said and cant get it right yet... anyone care to make a deb? or copy paste the exact text i need to throw into terminal?

---

### Post by mister_k81 on 2009-07-01
> **dcninja said:**
> tried it, here's result
cninja@dcninja-netbook:~$ cd xe-x86
dcninja@dcninja-netbook:~/xe-x86$ dir
install.sh  libxe.a  Makefile  manual.html  modules  rc  README.txt
dcninja@dcninja-netbook:~/xe-x86$ make
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
/usr/bin/ld: cannot find -lasound
collect2: ld returned 1 exit status
make: *** [xe] Error 1
dcninja@dcninja-netbook:~/xe-x86$

You're missing the developer packages for gtk+2.0 and for lasound. 

In order to install them you need to type (or copy and paste) this into the terminal: 

```
sudo apt-get install libgtk2.0-dev libasound2-dev
```

And as mentioned by Col-1023, you might also need to install the build-essentials package, which you can get by putting this into the terminal: 

```
sudo apt-get install build-essential
```

> **Col-1023 said:**
> 

I've also read that the command checkinstall will create a deb.




Information on CheckInstall here: [https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

Building with 'checkinstall' instead of 'make' will allow you to create a deb file for the program when compiling from source.

---

