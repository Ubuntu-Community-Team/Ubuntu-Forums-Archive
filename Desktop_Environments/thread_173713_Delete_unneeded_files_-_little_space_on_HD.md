---
title: "Delete unneeded files - little space on HD"
date: 2006-05-10
forum: Desktop Environments
---

### Post by neoaddict on 2006-05-10
What unneeded files can I delete off my HD so I can regain more space than just 370 MB?

---

### Post by meng on 2006-05-10
Wow that's a REALLY tough question to answer, in fact I'd venture to say it's impossible to answer (sensibly) the question as phrased.

---

### Post by bicchi on 2006-05-10
You might be able to squeeze a few megabytes by doing the following:
[LIST=1]
[*]Clear the browser cache in firefox (Edit -> Preferences -> Privacy -> Cache [Clear])
[*]Run: sudo apt-get clean 
[*]Run: sudo apt-get autoclean
[*]Remove all the thumbnails from: $HOME/.thumbnails/
[/LIST]
Those are the ones I can think from the top of my head. There might be some junk in the /tmp folder but that gets erased automatically at boot time.

---

### Post by Sutekh on 2006-05-10
You could clear the cache of install files that apt-get and Synaptic have downloaded.  Once they are installed you don't need them.  If you ever need them again, you can always download them.

This code will clean out the apt-get cache, autoclean only removes packages that are no longer downloadable
```
sudo apt-get autoclean
```
This code is less selective about what is removed, it just removes everything
```
sudo apt-get clean
```


Other than that, *uneeded* files may have to be your personal data.

---

### Post by neoaddict on 2006-05-10
My root (I'm the root user on the comp) and home folders are almost completely empty.

**EDIT:** Hehe... with clean, I got 300 MB back.  :D

Also, what libraries related to NVIDIA (don't use Nvidia cards), wifi and bluetooth can I remove?

---

### Post by Sutekh on 2006-05-10
If you are really strapped for space you should consider these links

[Ubuntu WIki - Low Memory Systems](https://wiki.ubuntu.com/Installation/LowMemorySystems) - which includes info on [IceWM](https://wiki.ubuntu.com/IceWM), [Fluxbox](https://wiki.ubuntu.com/Fluxbox) and XFCE (consider [Xubuntu!](https://wiki.ubuntu.com/Xubuntu))

[Ubuntu Wiki - Openbox](https://wiki.ubuntu.com/Openbox)

---

### Post by Dr. Nick on 2006-05-11
Also search the forums for clearing your kernel and other logs as they get huge over time and some of the info isnt needed.

---

### Post by neoaddict on 2006-05-11
If I read a topic correctly, do I install syslog-ng, uninstall the old log lib?

---

### Post by ComplexNumber on 2006-05-11
another viable suggestion that gives lots more space is to (given that you're not a developer) uninstall all current "devel" packages that _don't_ result in the removal of other packages that depend upon them.

---

### Post by Dr. Nick on 2006-05-11
[quote=neoaddict]If I read a topic correctly, do I install syslog-ng, uninstall the old log lib?[/quote] 
You can try that, Ive just seen that a few people reccomend syslog-ng over the default, ive never tried it though.

I participated in a nice discusion some months back on here about clearing hard drive space but for the life of me cant find it.

EDIT
[Here]("http://ubuntuforums.org/showthread.php?t=87342&highlight=delete+logs") is a thread that tells you how to properly clear the log files, not the one I was looking for but still a  good resource

---

### Post by neoaddict on 2006-05-11
Just checked my log directory, it's only 12 MB in total.  I've disabled the logging services via System -> Admin -> Services because I don't need them.

Also, is it possible to mount /usr onto my network and get Ubuntu to access it from there?

---

### Post by aysiu on 2006-05-11
```
sudo apt-get install deborphan
``` It'll track down all the packages that no other packages depend on--i.e., ones you can get rid of safely if you don't need them any more.

---

### Post by neoaddict on 2006-05-12
Is it safe to uninstall the Nvidia packages if you don't use them?

---

### Post by Dr. Nick on 2006-05-12
oops
see below

---

### Post by Dr. Nick on 2006-05-12
Should be, Just watch the dependencies removed. gtkorphan is a nice gui to deborpahn, You can get it from these forums

---

### Post by neoaddict on 2006-05-12
I should wait until Dapper is out, then I'll uninstall all those ubuntu_desktop packages that I really don't need.

Also, as I asked above, is there any way I can mount folders onto a network and get Ubuntu to access it from there?

---

### Post by neoaddict on 2006-05-13
Oh, how do you delete unneeded themes and screensavers?

---

### Post by Dr. Nick on 2006-05-13
[quote=neoaddict]Oh, how do you delete unneeded themes and screensavers?[/quote] 
Search synaptic for theme and screensaver. I marked mine for removal and It said it would free about 28mb total. You can probably remove all of the screensaver files installed but I would be careful which themes you choose to remove, you can probably do the accesibility themes but you dont want to uninstall them all.

I dont know about your network question :(

When removing just watch what else its going to remove and be careful

---

### Post by Dr. Nick on 2006-05-16
Here is a nice how-to for anyone insterested
[http://ubuntuforums.org/showthread.php?t=140920&highlight=gtkorphan](http://ubuntuforums.org/showthread.php?t=140920&highlight=gtkorphan)

---

