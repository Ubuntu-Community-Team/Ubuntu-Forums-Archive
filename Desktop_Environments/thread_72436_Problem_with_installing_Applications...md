---
title: "Problem with installing Applications.."
date: 2005-10-06
forum: Desktop Environments
---

### Post by abominable on 2005-10-06
I managed to install Kubuntu. But now I face problems installing the applications I need..
Firefox-Thunderbird:
Error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: no such file or directory.
Kdevelop
Checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

---

### Post by Knome_fan on 2005-10-06
How are you trying to install the apps?

If in anyway possible (and it should be possible with the apps you mention), use apt on the command line, or kynaptic to install what you need.

---

### Post by abominable on 2005-10-06
I use the terminal.I extract the files with tar, to the propper destination, I entered to the files, ex firefox and I press ./firefox-installer or ./firefox-instaler-bin. And then comes the error..
The same goes with thunderbird and Kdevelop..
How will I use apt??

---

### Post by Knome_fan on 2005-10-06
Open a terminal and then do:
sudo apt-get install thunderbird (to install thunderbird for example)
Also take a look here:
[https://wiki.ubuntu.com/AptGetHowto](https://wiki.ubuntu.com/AptGetHowto)
and make sure to check out the unofficial kubuntu guide:
[http://kudos.berlios.de/kf/kf1.html#swmgmt](http://kudos.berlios.de/kf/kf1.html#swmgmt)
Have fun! :D

---

### Post by abominable on 2005-10-06
I tried it and it said :
E: Couldn't find package thunderbird..

I even entered to the file where there is thunderbird, but I had the same error..

---

### Post by SGC on 2005-10-06
[QUOTE=abominable]I tried it and it said :
E: Couldn't find package thunderbird..
I even entered to the file where there is thunderbird, but I had the same error..[/QUOTE]
Open konsole from kmenu -> system, and type:
```
sudo kate /etc/apt/sources.list
```
When the file opens, enter the following two line:
```

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
```
Save the file and return to konsole and type the following:
```

sudo apt-get update
sudo apt-get install kdevelop mozilla-thunderbird mozilla-firefox

```

---

### Post by abominable on 2005-10-06
First of all, I am not connected to the internet..I can't configure Internet connection through linux..

I tried with mozilla-firefox..:

Package mozilla-firefox is not available, but is reffered to by another package.
This may mean that the package is missing, has been obsoleted, or is only avalaible from another source.
E: Package mf has no installation candidate.

I also tried with firefox-installer

E: Couldn't find package firefox-installer

The same with kdevelop and thunderbird

---

### Post by abominable on 2005-10-06
Ok don't bother.. They just told that I have to be connected to the Internet...Sorry for your time..

---

