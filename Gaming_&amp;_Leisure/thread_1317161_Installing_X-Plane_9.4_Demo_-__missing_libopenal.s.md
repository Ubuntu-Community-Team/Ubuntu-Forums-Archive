---
title: "Installing X-Plane 9.4 Demo -  missing libopenal.so.0 library"
date: 2009-11-06
forum: Gaming &amp; Leisure
---

### Post by Ken-san on 2009-11-06
Hey all, I'm having a problem with installing X-Plane demo on Karmic (x64). Upon running 
```
./X-Plane\ Demo\ Installer\ Linux
```
it says
```
./X-Plane Demo Installer Linux: error while loading shared libraries: libopenal.so.0: cannot open shared object file: No such file or directory
```
even though I did the following
```
sudo apt-get install libopenal1
sudo ln -s /usr/liblibopenal.so.1.8.466 /usr/lib/libopenal.so.0
```

Any ideas?

---

### Post by ihatenicks on 2009-11-08
Same problem here in MINT
libopenal is installed but...!

---

### Post by hardwarehank on 2009-12-09
Works on Karmic 64-bit:
```
sudo ln -s /usr/lib32/libopenal.so.1.8.466 /usr/lib32/libopenal.so.0
```

---

### Post by Flymo on 2009-12-21
Greetings, and thanks for the idea - on Karmic Xubuntu I had to patch your command fractionally to accommodate the file locations:

```
sudo ln -s /usr/lib/libopenal.so.1.8.466 /usr/lib/libopenal.so.0
```

These libraries seem to move around as development proceeds, so it is worth looking for missing items - I used Synaptic to finger the install location of **libopenal**, and (interestingly) found a **libopenal.so.1** link to the actual library already in place.  Think the system that Austin uses to put the Linux version together may be a rev or two behind the leading edge...? 

Anyhow - the Installer now seems to be up and running, many thanks!

All the best, Ben

---

### Post by opensourcederry on 2009-12-25
This link below deals with installing on 32bit Karmic but also covers the openal error so you may be able to get some pointers.

[http://www.ilovelinux.co.uk/xplane910-1.php](http://www.ilovelinux.co.uk/xplane910-1.php)

osd

---

### Post by Yfrwlf on 2010-03-22
Damn, it's half-assed attempts like this that give Linux a bad name.  Seriously, either help push for some kind of standards so that a distro will know how to install that library using some standardized naming convention or whatnot that will match up even with distro-specific custom packages which contain it, or include the library in the download.  I know everyone loves to ignore me when I complain about packaging standards being important, but, this is one of the reasons why.

Never going to win over normal desktop users with issues like this.

---

### Post by rdingram on 2010-06-02
For those looking to install X-plane in 10.04, use the following to fix the missing dependency.

```
sudo ln -s /usr/lib/libopenal.so.1.12.854 /usr/lib/libopenal.so.0
```

---

### Post by Robbyjhb on 2010-06-28
Do not know what the hell is going on with ubuntu this is what I get running , 32bit ubuntu 10.04
robert@ubuntu:~$ [COLOR=Red][B]sudo ln -s /usr/lib/libopenal.so.1.12.854 /usr/lib/libopenal.so.0
ln: creating symbolic link `/usr/lib/libopenal.so.0': File exists[/B][/COLOR]
robert@ubuntu:~$ cd Desktop
robert@ubuntu:~/Desktop$ ./&#8221;X-Plane DVD Installer Linux&#8221;
bash: ./&#8221;X-Plane: No such file or directory
  I am really getting eager to get x-plane installed now.

Robert

---

### Post by Malcolm Jackson on 2010-08-25
> **rdingram said:**
> For those looking to install X-plane in 10.04, use the following to fix the missing dependency.
 
```
sudo ln -s /usr/lib/libopenal.so.1.12.854 /usr/lib/libopenal.so.0
```
 
 
Hi rdingram, Many thanks for the info. Put your code into terminal, switched off the PC, and when I rebooted I managed to get  X-Plane running on Ubuntu. Brilliant. Thanks for taking the time to help. Nearly 2 weeks of frustration and now sorted.
Best regards.

---

### Post by HellionDarkLord on 2010-08-29
This isn't working for me at all.

libopenal.so.0 => not found

even though I tried the symbolic link thing.  I am on linux mint 64bit so that may make all the difference.

I tried adding /lib32/lib....  to the symbolic link, but that didn't work either.

I'm thinking of just going back to 32bit linux where everyrthing works :(

---

