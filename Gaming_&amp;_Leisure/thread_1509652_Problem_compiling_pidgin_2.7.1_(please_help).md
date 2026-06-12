---
title: "Problem compiling pidgin 2.7.1 (please help)"
date: 2010-06-14
forum: Gaming &amp; Leisure
---

### Post by beliyyal on 2010-06-14
Hi guys, I been having a problem compiling the latest version of pidgin, 2.7.1, and I was wondering if someone could help me out? This is what I keep getting in terminal:

```
checking for XScreenSaverRegister in -lXext... no
checking for XScreenSaverRegister in -lXss... no
configure: error: 
XScreenSaver extension development headers not found.
Use --disable-screensaver if you do not need XScreenSaver extension support,
this is required for detecting idle time by mouse and keyboard usage.
```

I am not sure what the problem is. I have looked in synaptic, cannot find any xscreensaver dev files. I am at a loss. Any help would be much appreciated.

---

### Post by Linuxforall on 2010-06-14
While you may have a reason to compile Pidgin, the pidgin developers ppa contains latest pidgin by default and you may wanna look into that as well.

[https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa)

---

### Post by beliyyal on 2010-06-14
> **Linuxforall said:**
> While you may have a reason to compile Pidgin, the pidgin developers ppa contains latest pidgin by default and you may wanna look into that as well.

[https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa)

Thanks, I went to the download section in the pidgin website, and one of the options was PPA. I clicked it and it downloaded a .deb file (which is weird, because usually you have to add the PPA string into the software sources) but I didn't really think much of it, I just came over from 8.04 and things are....pretty different on 10.04, to say the least.

---

### Post by wesleybishop on 2010-06-14
Are you just trying to install pidgin?

---

### Post by beliyyal on 2010-06-14
> **wesleybishop said:**
> Are you just trying to install pidgin?

No, trying to install the newest version. I got it installed now, but I am still having problems with the voice/video chat plugin. For some reason I cannot activate the plugin. Oh well, guess I'll get Gyache for webcam chat.

---

### Post by maedox on 2010-06-15
As mentioned before me, if you
```
sudo apt-add-repository ppa:pidgin-developers/ppa
```
you will get the latest pidgin from their repo.
Use apt-get update/upgrade/install as usual, or synaptic if that's what you prefer.

---

### Post by SpEcIeS on 2010-07-24
Did you apply the following before compiling?

```
sudo apt-get build-dep pidgin
```

---

