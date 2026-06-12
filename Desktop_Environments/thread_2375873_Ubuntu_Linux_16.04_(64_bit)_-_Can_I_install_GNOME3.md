---
title: "Ubuntu Linux 16.04 (64 bit) - Can I install GNOME3?"
date: 2017-10-28
forum: Desktop Environments
---

### Post by la.khan on 2017-10-28
Hi all,

Recently, I read that, beginnning 18.04 LTS, Canonical plans to make GNOME3 as the default desktop environment, ditching Unity.

Currently, I have Ubuntu Linux 16.04 LTS (64 bit) installed. Can I install GNOME3 on this? Will GNOME3 work with UL16.04 (64 bit)?

```
dpkg -l libgnome2-common
2.32.1-5ubuntu1

unity --version
unity 7.4.0

uname -r
4.4.0-97-generic
```

This page [https://wiki.ubuntu.com/UbuntuGNOME/GetUbuntuGNOME](https://wiki.ubuntu.com/UbuntuGNOME/GetUbuntuGNOME) has a GNOME available for UL 16.04 (64bit). Any idea what version of GNOME is this? GNOME2 or GNOME3?

Is there a thread that has pros & cons of installing GNOME3 on an older version of UL? If this was discussed in a earlier thread, please point me to it.

Thanks for the reply!

---

### Post by howefield on 2017-10-28
The new desktop environment has shipped with Ubuntu 17.10, and is a bit different to what you'd get with the, eg, 17.04 UbuntuGnome as you link above. I'd suggest creating a live USB with 17.10 and taking it for a spin, perhaps even a Live with persistence so you can play about with it more meaningfully.

---

### Post by mark bower on 2017-10-28
@la.kahn

I would assume that you can install the gnome classic desktop on 16.04LTS/64bit.  I installed gnome on my 16.04LTS/32 bit using either the Software Center or "sudo apt-get install gnome-session-flashback"(I do not remember which method).  It is the nicest appearing of the gnome desktops I have ever used.

---

### Post by la.khan on 2017-10-29
@howefield: thanks for the suggestion. That's one of my options [IMG]https://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]

@mark bower: When I started looking for more information on Google, I found a few sites that answered my questions.

[HTML]https://askubuntu.com/questions/766071/install-gnome-shell-on-ubuntu-16-04?rq=1[/HTML]
[HTML]https://askubuntu.com/questions/817319/how-do-i-get-this-gnome-desktop-in-ubuntu-16-04?rq=1[/HTML]

If & when I am ready, it looks like ```
sudo apt-get install ubuntu-gnome-desktop
``` will install GNOME desktop.

BTW, UL16.04 has GNOME 3.18 by default, so GNOME 3 DE should work in UL 16.04 (64 bit).

If I decide to install GNOME 3, any idea what this does to my
1. folders/directories & files?
2. applications that come with UL 16.04 (Firefox 56, Libre office, gedit, evince PDF reader etc)?
3. applications that I installed (Brave browser, Eclipse Neon, Master PDF editor, Apache, MySQL, GIMP etc)

Anything I need to watch out for?

---

### Post by kurt18947 on 2017-10-29
I don't know if "standard" gnome apps such as maps and photos will be installed or not but I'd surprised if any existing apps are disabled or removed. Will they look different? Perhaps, I don't have experience there. I've used Ubuntu-Gnome since Unity's debut and recently installed 17.10. There are visual differences between 16.04 Ubuntu-Gnome and 17.10 but I don't see much change at all 'under the hood'. I've installed other desktops such as XFCE on Ubuntu-Gnome and was able to select the desktop of choice on the login screen.. As always when making a substantial change, back up any "My Significant Other will kill me if I lose this" data beforehand.

---

### Post by meetdilip on 2017-10-29
The last I heard, Gnome DE comes with their own version of Nautilus. I read a blog saying that it could pose you an issue if you wish to remove Gnome DE. That is one reason why I stayed with Unity.

---

### Post by la.khan on 2017-11-01
Hi all,

I have installed Ubuntu Gnome 3.18 and everything looks fine, as of now. Thanks for your replies!

However, I do notice that my laptop takes longer to boot up :confused: Prior to installing Gnome, with regular UL 16.04, my laptop displayed login screen in less a min; now it takes a couple of minutes. Any idea why? BTW, I increased my RAM from 4 GB to 8 GB earlier this week. My applications respond faster :) but my OS (UL 16.04 + UG 3.18) is running slower :(

---

