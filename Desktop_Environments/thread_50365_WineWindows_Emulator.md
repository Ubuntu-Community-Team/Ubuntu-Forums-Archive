---
title: "Wine/Windows Emulator"
date: 2005-07-20
forum: Desktop Environments
---

### Post by Pat77 on 2005-07-20
I ran synaptic to get Wine, but either its not installed or i dont know where its at...I want to run Ventrilo and STEAM in linux...those are the only two windows programs i cant live without...any help on installing Wine or another Emulator would be great...
Thanks, 
Pat

---

### Post by exile on 2005-07-20
Can you tell me what you see when you type 'locate wine' at the prompt (without the quotes)?

You might have to do sudo updatedb if you haven't run it recently.

---

### Post by Pat77 on 2005-07-20
it says this:
```
/usr/share/icons/hicolor/48x48/apps/wine.png
/usr/share/icons/Human/scalable/apps/wine.svg
``` 
then i go look at this directory and they are both obviously just icons...

---

### Post by exile on 2005-07-20
It doesn't look like it is installed.

can you try 

sudo apt-get install wine

and tell me what it says?

---

### Post by Pat77 on 2005-07-20
well i am out of Linux for the night...but i will post tomorrow...thanks...

---

### Post by Pat77 on 2005-07-20
it says:
```
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate
```

---

### Post by bored2k on 2005-07-20
[QUOTE=Pat77]it says:
```
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate
```[/QUOTE]
 Steam as in Counter-Strike ? That's really easy.

Once you download Steaminstall.exe from Steampowered.com, in a terminal run
wine Steaminstall.exe

That it is

---

### Post by cutOff on 2005-07-20
[QUOTE=Pat77]it says:
```
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate
```[/QUOTE]
Could you post your sources.list??

$ cat /etc/apt/sources.list

You should have something like this

```
## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

---

### Post by themelvin on 2005-07-20
I installed Wine but my keyboard is not recognized. It' s a BTC 8190A. When I tried to install Photoshop i was unable to write the serial number. I changed the keyboard's layout to Logitech and MS but then in Wine only beeps, if it is set to Generic 104 it doesn't beep but it also doesn't work. Does anybody know what's wrong?

---

### Post by nanolinux on 2005-07-20
Hello,

     This is my first time on Ubuntuforums.  I am having similar difficulties installing Wine with ubuntu.  I used synaptic, however I could not download winetools properly.  I did however go into the root and ran 'apt-get install wine'.  I get most of the files, however I am still without a wine icon.  If i search the files and run exe. text files, I am able to get into wine, which prompts me to configure wine since I am a new user.  When I try to do that, it says I am missing some files and so the circle begins again.

Any ideas?

Thanks.
nl

---

### Post by pompeyjohn on 2005-07-21
yup, same problem here.

---

### Post by jatos on 2005-07-21
Right guys and gals, you may want to head over to [www.winehq.com](www.winehq.com) where you find specific instructions for installing WINE on ubuntu (click the download link down site).

Though one thing, whenever I run Wine on kubuntu-desktop, I see the Wine icon on the taskbar with the sand time then after it just disappears, anyone know why?

---

### Post by Terracotta on 2005-07-21
I have no idea why it does that, but sometimes synaptic does that too, or when I want to edit a file as root, just before it's about to ask the password it hangs and does exactly the same as wine does on your desktop, I think it's a bug in kubuntu-desktop itself with the  root password, not a wine problem. Trying again and one of the times it  will work :-), at least that's what I do, I hope they fix that problem in the next release.

---

### Post by Mr_Grieves on 2005-11-13
I made a little mini-mini-howto on getting Steam/CS 1.6 running in Ubuntu with wine.
[http://cslinux.hacka.net](http://cslinux.hacka.net)

---

