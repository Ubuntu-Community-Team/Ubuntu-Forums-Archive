---
title: "Couple Questions Regarding Adept"
date: 2006-01-09
forum: General Help
---

### Post by Glass Casket on 2006-01-09
So I'm trying to install Firefox in Kubuntu with Adept, but it gives me an error. It seems to download every file fine, but it gives me this error once it depackages a couple files: 'There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages.'

Also, when I start up Adept, it says that it's in read only mode since I didn't log into it with root.

So my question is how can I log into root for Adept in order to fix this problem. If that's the solution.

Thanks.

***Also, is there a Kubuntu guide similar to the Ubuntu Guide listed at: [http://www.ubuntuguide.org](http://www.ubuntuguide.org)***

---

### Post by aysiu on 2006-01-09
Alt-F2 ```
kdesu adept
```

---

### Post by Glass Casket on 2006-01-09
I still get the same error.

---

### Post by aysiu on 2006-01-09
You shouldn't ever have to log in as root.
Did you do an expert install by chance?

What about when you try to apt-get from the command-line?
Alt-F2 ```
konsole
``` ```
sudo apt-get update
sudo apt-get install firefox
```

---

### Post by Glass Casket on 2006-01-10
glasscasket@GlassCasket:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

---

### Post by aysiu on 2006-01-10
[QUOTE=Glass Casket]glasscasket@GlassCasket:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory[/QUOTE] Maybe [this](http://www.linuxquestions.org/questions/showthread.php?t=394701) might help?

P.S. You can't run apt-get while Adept is open. I don't know if you have Adept open.

---

### Post by feathers on 2006-01-10
You have either no administrator rights or another process is using dpkg. Have you rebooted your computer? Try this and the type sudo apt-get update again.

---

### Post by Glass Casket on 2006-01-10
Adept works now, thanks.

But now new problems arise when I try to install my ATI video card drivers.

glasscasket@GlassCasket:~$ sudo apt-get install xorg-driver-fglrx
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

From using [http://doc.gwos.org/index.php/Install_ATI_driver](http://doc.gwos.org/index.php/Install_ATI_driver)

Maybe I have to kill some process?

---

### Post by Thirsteh on 2006-01-10
You can't have Adept, Synaptic or any other of the apt-get utilities open when you do that command. Close them and try again.

---

### Post by Glass Casket on 2006-01-10
Thanks for the reply and it helped, but now while I install it, there at several questions. 

Once it's done isntalling, it dosen't seem as if it worked:

glasscasket@GlassCasket:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

I have an ATI X300 PCIE.

---

### Post by feathers on 2006-01-10
Maybe you have to reconfigure X. Type sudo dpkg-reconfigure xserver-xorg and answer the configuration questions.

---

### Post by Glass Casket on 2006-01-10
[QUOTE=feathers]Maybe you have to reconfigure X. Type sudo dpkg-reconfigure xserver-xorg and answer the configuration questions.[/QUOTE]

I tried it again and got: xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.200601101222

There are a pretty long list of questions that I don't know what to put the answer as.

Maybe the best way is to download the drivers from the ATI website, but I can't seem to find it at the moment.

---

