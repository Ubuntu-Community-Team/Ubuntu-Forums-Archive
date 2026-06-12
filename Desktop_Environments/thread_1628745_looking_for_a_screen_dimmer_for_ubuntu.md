---
title: "looking for a screen dimmer for ubuntu"
date: 2010-11-23
forum: Desktop Environments
---

### Post by rdangelojp7 on 2010-11-23
Hello there (sorry if this topic seems repetitious), I'm looking for a software that can reduce screen brightness below what Power Management allows. For Windows there's the free DimScreen program ([http://www.raymond.cc/blog/archives/2008/08/13/how-to-dim-or-increase-the-brightness-of-laptop-or-notebook-lcd-screen/](http://www.raymond.cc/blog/archives/2008/08/13/how-to-dim-or-increase-the-brightness-of-laptop-or-notebook-lcd-screen/)), but I have not been able to find the equivalent for Ubuntu Linux. Any suggestions will be appreciated (my eyes will be especially thankful!)

---

### Post by koleoptero on 2010-11-23
I don't know if it's what you're asking but you can use redshift. You can install it from their ppa by opening a terminal and typing:

sudo add-apt-repository ppa:jonls/redshift-ppa
sudo apt-get update
sudo apt-get install redshift

Then run it from the Accessories submenu in applications, or press alt+f2 and run redshift.

You can also add an applet to the panel that sets the screen brightness by right-clicking on the panel on an empty space, selecting "add to panel" from the dropdown menu, and then selecting the appropriate applet (I don't remember its name exactly and I can't check now, but it's quite self-descriptive). That will only dim the display manually though, not automatically. Plus if you have a desktop PC and not a laptop I don't know if it will work.

Hope these help.

---

### Post by stinkeye on 2010-11-23
I use RedshiftGUI which reduces eye strain.
Same as Redshift but with a customization GUI.
[**_[COLOR="DarkRed"]http://www.webupd8.org/2010/07/redshiftgui-protects-your-eyes-when.html[/COLOR]_**]("http://www.webupd8.org/2010/07/redshiftgui-protects-your-eyes-when.html")

---

### Post by bobcollard on 2010-11-23
> **rdangelojp7 said:**
> Hello there (sorry if this topic seems repetitious), I'm looking for a software that can reduce screen brightness below what Power Management allows. For Windows there's the free DimScreen program ([http://www.raymond.cc/blog/archives/2008/08/13/how-to-dim-or-increase-the-brightness-of-laptop-or-notebook-lcd-screen/](http://www.raymond.cc/blog/archives/2008/08/13/how-to-dim-or-increase-the-brightness-of-laptop-or-notebook-lcd-screen/)), but I have not been able to find the equivalent for Ubuntu Linux. Any suggestions will be appreciated (my eyes will be especially thankful!)
Right-click your desktop and open Desktop Settings. OR, You might try Brightside in Synaptic Package Manager.

---

### Post by rdangelojp7 on 2010-11-23
Thanks for the responses! I just tried ```
sudo add-apt-repository ppa:jonls/redshift-ppa
``` and I got ```
sudo: add-apt-repository: command not found
``` This is actually the second time this has happened. Anyways I'll do some searching around to see what's wrong. Actually I have Ubuntu 9.04 if that makes a difference. Meanwhile I'll look at stinkeye's GUI solution. And I did get the brightness control applet going, so now it's better than before. But when I right-click anywhere on my desktop I do not see desktop settings, again maybe due to a different ubuntu version? I'm also going to checkout Brightside.
Thanks for the responses again

---

### Post by koleoptero on 2010-11-25
Well the problem with adding the repository for redshift is indeed the fact that you have 9.04, that command was added in 9.10 :)

Install redshift GUI as suggested by stinkeye, it's easier to configure, by clicking on this link and opening the file: [CLICKY]("https://gith*******/downloads/maoserr/redshiftgui/RedshiftGUI-0.2.1-Linux-i686.deb")

---

### Post by rdangelojp7 on 2010-11-25
Well I finally upgraded my 9.04 to 9.10, but something's going wrong, everything is running super super slow (I'm actually writing this on my Vista)!!! I'm going to make another thread about this.
I did somehow manage to install Redshift though, using the initial procedure that you pointed out, but nothing happened when I did Alt-f2 run redshift, and there were no redshift icons in the accessories menu, but when I just typed ```
$ redshift
``` on the command line, the redshift program prompted me for latitude/longitude coordinates, and ```
$ redshift -h
``` did bring up the help menu, so I think from here I can figure it out. Thanks again.
Now on to my next thread. :cry:

---

### Post by Helkaluin on 2010-11-25
No no no. Redshift is not a dimmer. It's a program that alters your colour temperature according to time.

I don't quite know the dimming part. The Gnome power manager way to do it actually reduces the back light for LCDs. A quick hack to reduce brightness beyond that is to actually reduce system-wide brightness via your display card driver's configuration tools.

---

### Post by stinkeye on 2010-11-26
> **Helkaluin said:**
> No no no. Redshift is not a dimmer. It's a program that alters your colour temperature according to time.

True dat.
But the OP was looking for something to reduce eyestrain, which is exactly 
what redshift does. You can disable the time adjust and use a manual setting.

---

### Post by SpotHT on 2010-11-26
You can try the **DDCcontrol **tool

```
sudo apt-get install gddccontrol


```

---

### Post by koleoptero on 2010-11-26
> **Helkaluin said:**
> No no no. Redshift is not a dimmer. It's a program that alters your colour temperature according to time.

I don't quite know the dimming part. The Gnome power manager way to do it actually reduces the back light for LCDs. A quick hack to reduce brightness beyond that is to actually reduce system-wide brightness via your display card driver's configuration tools.

The latest redshift-gui can dim the screen too. Albeit not automatically as far as I know.

---

### Post by Defrector on 2010-11-26
Ubuntu appears to support the typical keyboard-shortcuts for screen dimming out-of-the-box for most rigs. On mine it is Fn+F6 for darker and Fn+F7 for brighter.

---

### Post by rdangelojp7 on 2010-11-26
>  No no no. Redshift is not a dimmer. It's a program that alters your colour temperature according....
really? I didn't know that, I thought reducing temperature and dimming had the same meaning. I'll try redshift anyways (and also Fn+F6/F7, once I get Koala going, :-x), but I'm really looking for a dimmer, like DimScreen for windows, if redshift allows manual setting that should be great.
Now about the card driver configuration tools and gddccontrol, one of the reasons I started this thread was because I was unsuccessful in installing ddccontrol, which seems to be the best thing for brightness control. During the installation process while following ddccontrol's homepage instructions, two of the several requirements were: 1) loading the so called i2c-dev module which I did successfully, and 2) downloading the framebuffer driver for my Toshiba Satellite, which I could not find anywhere. I also did try ```
sudo apt-get install gddccontrol
``` and brought up the initial ddccontrol window, which had a message saying that the i2c-dev module and framebuffer driver need to be installed. So I'll probably be researching this for a while, or wait until future ddccontrol versions are compatible with my monitor. A back door to my card driver's configuration tools sounds just as good as ddccontrol, but beyond my present abilities (meaning more research)!!

---

### Post by tom4everitt on 2010-11-27
Wow, did you try RedShiftGUI? 

[http://www.webupd8.org/2010/07/redshiftgui-protects-your-eyes-when.html](http://www.webupd8.org/2010/07/redshiftgui-protects-your-eyes-when.html)

Works wonders as a dimmer, and I think that the redshifting can be a good thing too. (gddccontrol didn't work for me, same problem as the OP.)

---

### Post by rdangelojp7 on 2010-11-29
Redshift is boss!! actually the regular command version is simple enough. My eyes are incredibly grateful!

---

