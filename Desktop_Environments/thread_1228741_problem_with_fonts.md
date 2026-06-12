---
title: "problem with fonts"
date: 2009-08-01
forum: Desktop Environments
---

### Post by stonecoldjha on 2009-08-01
hi.......i've been using kde4.2 for quite a while on ubuntu 8.10............and i like it so much,except for a minor glitch,the fonts look ugly...........and sometimes,they look disfigured as is clear in the screenshots(this happens quite often,and the fonts are restored to their original look after sometime).is there anything that i can do to get rid of this?also,i want my kde to render fonts as smooth and good looking as that in gnome or vista....i would really appreciate if i am helped out!

---

### Post by Zorael on 2009-08-01
Could this be a driver issue?

Do you have an Nvidia card running with the proprietary driver, by any chance?

---

### Post by stonecoldjha on 2009-08-01
yup,i have an nvidia geforce 6200 running on a proprietary driver.but i never have this problem with gnome which renders fonts just as good as i want it to...

---

### Post by ~sHyLoCk~ on 2009-08-01
Goto system settings->Font Installer and see if you can see the font previews. Also goto Appearance->Fonts and try changing the fonts and see if it fixes.

---

### Post by Zorael on 2009-08-01
Is this it? [https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/334657](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/334657)

If so, disabling subpixel hinting or changing it to horizontal RGB/BGR should work around it.
```
This bug was fixed in the package qt4-x11 - **[COLOR="DeepSkyBlue"]4.5.0-0ubuntu4.1[/COLOR]**

---------------
qt4-x11 (**[COLOR="DeepSkyBlue"]4.5.0-0ubuntu4.1[/COLOR]**) jaunty-**proposed**; urgency=low

  * Add kubuntu_10_disable_ft_lcdfilter.diff from suse to fix font corruption
    on vertically-hinted LCD screens (LP: #334657)

 -- Jonathan Thomas <echidnaman@kubuntu.org> Thu, 23 Apr 2009 08:29:55 -0400
```
It looks like it's in jaunty-updates now, though?

The packages.ubuntu.com page for  [libqt4-opengl in jaunty-updates](http://packages.ubuntu.com/search?keywords=libqt4-opengl&searchon=names&suite=jaunty-updates&section=all) (which is a part of qt4-x11) says the available version is **[COLOR="DeepSkyBlue"]4.5.0-0ubuntu4.1[/COLOR]**.

Do the following in a terminal to see which you have installed, and what versions are available.
```
$ apt-cache policy libqt4-opengl
```

---

### Post by ellgor on 2009-08-01
Hi, 

If you are still having problems then try this little whizz I found at TomUbuntu:

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <match target="font">
    <edit name="autohint" mode="assign">
      <bool>true</bool>
    </edit>
  </match>
</fontconfig>

make a file in your home directory and copy this into it as 
.font.conf 
it will need a restart to enable it and once it has , I found that the text leaped out and if I'm not mistaken some apps that were misbehaving seemed to have calmed down, I think, hope this helps.

Regards, Ellgor.

---

### Post by stonecoldjha on 2009-08-01
the last thing seemed to work for a while,but a few moments ago fonts looked screwed up again as you can see in my latest screenshot.

---

### Post by krazyd on 2009-08-01
This happens for me too, just not on my ATI graphics system.
There's a thread here: [http://www.nvnews.net/vbulletin/showthread.php?t=130117](http://www.nvnews.net/vbulletin/showthread.php?t=130117)

---

### Post by ellgor on 2009-08-02
> **stonecoldjha said:**
> the last thing seemed to work for a while,but a few moments ago fonts looked screwed up again as you can see in my latest screenshot.
Hi again,

You  say the tip worked for a while, did it stop after a shutdown?, if so the last settings are not being saved at shutdown, a simple test, remove the little program and re-install it restart and see if it works, if it does you'll know its not being saved, hope this helps.

Regards, Ellgor.

---

### Post by stonecoldjha on 2009-08-03
can u tell me if the file is to be named "fonts.conf" or "font.conf"?

---

### Post by ellgor on 2009-08-04
Hi again

the file is named

.font.conf

be sure to include the dot at the beginning and in the middle,

Regards, Ellgor.

---

### Post by Zorael on 2009-08-04
.font**_s_**.conf, no?

```
FONTS-CONF(5)                                                    FONTS-CONF(5)

NAME
       fonts.conf - Font configuration files

SYNOPSIS
          /etc/fonts/fonts.conf
          /etc/fonts/fonts.dtd
          /etc/fonts/conf.d
          **~/.fonts.conf**

DESCRIPTION
       Fontconfig is a library designed to provide system-wide font configura&#8208;
       tion, customization and application access.
```

---

### Post by oldfred on 2009-08-04
Even more info and config files:
[http://hawn.be/tag/ubuntu-fonts-msttcorefonts-microsoft-fonts-tahoma-arial-times-new-roman/](http://hawn.be/tag/ubuntu-fonts-msttcorefonts-microsoft-fonts-tahoma-arial-times-new-roman/)
I have not tried then yet.

---

