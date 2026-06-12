---
title: "Wine -&gt; Windowsupdate"
date: 2005-12-15
forum: Desktop Environments
---

### Post by Ruskie on 2005-12-15
Hello.

I have a working wine installation, so I have windows explorer. Can I run the windows update applet? What would happen to wine and linux if I allow it to run?

Thank you
Marco

---

### Post by f1dave on 2005-12-15
Hello Marco,

This is just a guess, but I don't think running the windows update applet with wine will do you much good at all. It certainly won't update linux, and it is unlikely going to be able to update windows, especially if windows is mounted on a read only partition. Your best bet would just be to run it from windows itself.

---

### Post by Ruskie on 2005-12-16
Lol, no no, I didn't think it could update Linux! The thing is, I have a fake Windows installation on "drive_x", with IE6 on it... One of the first perverse thing I did when I had Linux up and running was to go to windowsupdate site with konkueror, only to see the site complaining I don't have IE6. Now that I have it, windowsupdate.com is tricked into believing I have windows, and tries to install its applet. I just wanted to know if letting him go on would screw the Wine installation, or would stop as soon as it starts... or what. :)

---

### Post by kenweill on 2005-12-16
[QUOTE=Ruskie]Lol, no no, I didn't think it could update Linux! The thing is, I have a fake Windows installation on "drive_x", with IE6 on it... One of the first perverse thing I did when I had Linux up and running was to go to windowsupdate site with konkueror, only to see the site complaining I don't have IE6. Now that I have it, windowsupdate.com is tricked into believing I have windows, and tries to install its applet. I just wanted to know if letting him go on would screw the Wine installation, or would stop as soon as it starts... or what. :)[/QUOTE]

Ruskie,

Im interested on having fake Windows installation. How did you do it?
Im currently using Windows XP, on the server, because my current internet connection works only on Windows. Its a requirement. It needs an accelerator/driver to connect to the internet. And its windows based only.

I have tried running the accelerator installer, but it asks for Windows, and IE6.

**So how did you do the fake Windows Installation?**

---

### Post by Ruskie on 2005-12-16
Well, I did nothing special. As a matter of fact, one could argue it's not even a "fake Windows installation", but it does what I need...

Simply install wine: sudo apt-get install wine
In case you don't know, it's... well, a layer for windows compatibility: actually, it allows you to run win32 executables on Linux, emulating Windows DLLs.
To do this, it fakes a windows "drive_c" in which you can install your windows program. You could run programs in your windows partition but in my experience they often have problems with their settings.

If you choose to try wine, I recommend to install also the package winetools, and as soon as you have installed the packages, run "winetools": it configures your wine installation and helps you downloading some basic windows dll you will need.

Most recent version of Wine can be downloaded in its own repository. Just add the following lines to your /etc/apt/sources.list:
```

#wine
deb http://wine.sourceforge.net/apt/ binary/ 
deb-src http://wine.sourceforge.net/apt/ source/ 
```
And then run Synaptic to get the packages.

Hope this helps
Marco

---

### Post by kenweill on 2005-12-16
k thanx alot.
I'll try it.

thanx for the info.

---

### Post by Ruskie on 2005-12-16
No problem. Let me know if it does what you need!
Marco

---

### Post by burningbed on 2006-01-02
I've tried running Windows Update from IE running in Wine and it didn't do anything ... IE just hangs.

---

### Post by newuser111 on 2006-01-02
in fact, you can connect to the windowsupdate site using IE6 in wine but it doesn't work, I don't see the point in doing it anyway, since its not a real windows installation.  If you want to use windows update, you could install a real windows installation using vmware or something similar, wine is not a complete windows installation only a compatibility layer

IE6 and media player 7 can be installed in wine however

---

### Post by JamesNorris on 2006-01-03
No, it won't work, IE will get as far as starting to download the updates, but then it goes straight to "the installation of these updates has failed" page.

---

