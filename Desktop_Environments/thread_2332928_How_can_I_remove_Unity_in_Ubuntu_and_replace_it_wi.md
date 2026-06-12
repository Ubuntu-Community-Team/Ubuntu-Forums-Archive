---
title: "How can I remove Unity in Ubuntu and replace it with the Trinity Desktop Environment?"
date: 2016-08-05
forum: Desktop Environments
---

### Post by fromwin2lin on 2016-08-05
I want to COMPLETELY REMOVE Unity from Ubuntu and replace it with the Trinity Desktop environment. Any suggestions?

Thanks.

---

### Post by howefield on 2016-08-05
Thread moved to the "*Desktop Environments*" forum.

---

### Post by &amp;KyT$0P# on 2016-08-05
Yes, instead of starting with Ubuntu start with something like Lubuntu or Xubuntu so that you aren't (basically) forced to keep parts of Unity around for things to work.

Also, I wouldn't log in a GUI if it's going to get purged, instead use Ctrl-Alt-F1 (or through Ctrl-Alt-F6) to get into a console / terminal-only login from which you can purge GUI-related stuff and install Trinity without worrying about what happens to your logged-in session

---

### Post by Frogs Hair on 2016-08-05
The Trinity repository info is available at the link. I have never attempted removing Unity and you might get TDE up and running before you start removing Unity. Synaptic is great tool for package removal if you don't have it installed. TDE support is available on IRC if you run into problems.

[https://wiki.trinitydesktop.org/UbuntuInstall#For_Xenial_.28Ubuntu_16.04_LTS.29](https://wiki.trinitydesktop.org/UbuntuInstall#For_Xenial_.28Ubuntu_16.04_LTS.29)

---

### Post by ajgreeny on 2016-08-05
It will be a lot cleaner to install the minimum-install CD version of ubuntu [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) and then add whatever you want to it.

It is a bit more involved than using a GUI for installing the OS if you can not, or do not like to use the command-line, but removing unity is not so simple as running ```
sudo ap-get remove unity*
```
I admit I did not know the trinity desktop, but have just found that it is a fork of KDE3, which I used and enjoyed many years ago.  However, I am not sure that trinity is still being developed and you may have problems installing it on the current versions as the most recent info I can find is for Lucid (10.04), now long out of support, and maybe precise (12.04).

EDIT:
I see Frogs Hair has found more up-to-date info so it may be worth a try.

---

### Post by ajgreeny on 2016-08-08
Just a quick update:

I have just installed trinity-desktop to a minimum-install CD version I have installed in VBox.
All went very well and I now have a fully working trinity-ubuntu 16.04.

Interestingly I now find that I do not like KDE as much as I did in the past, partly because I do not remember how to do things in KDE any more.  However, this was just an academic exercise to see if I could do it in the manner I suggested to you as the best way and I do not need to bother with this any further.

Back to Xubuntu for me!

---

### Post by Geoffrey_Arndt on 2016-08-13
Well, Trinity DE will make us feel young again . . . like we're back in the 90's!!

---

