---
title: "integrated graphics vs dedicated graphics card (ON / OFF)"
date: 2014-10-29
forum: Gaming &amp; Leisure
---

### Post by ricak on 2014-10-29
Hello all
I have the Lenovo U430 touch (i7-4510u *gb ram and 730m nvidia card)
If I go to Additional Drivers and then select the recommended "Nvidia Current" driver it will install the correct version on my system.

If I then do this :```
[COLOR=#333333][FONT=UbuntuRegular]To install bumblebee in Ubuntu 14.04, run these commands in terminal[/FONT][/COLOR][INDENT]sudo apt-get install bumblebee bumblebee-nvidia primus nvidia-331
[/INDENT]
[COLOR=#333333][FONT=UbuntuRegular]Now you have to install Bumblebee GUI to manage apps to be opened using nVidia. Here is the instructions:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Install Python App Indicator:[/FONT][/COLOR]
sudo apt-get install python-appindicator
[COLOR=#333333][FONT=UbuntuRegular]Install Git:[/FONT][/COLOR]
sudo apt-get install git
[COLOR=#333333][FONT=UbuntuRegular]Make a directory for git:[/FONT][/COLOR]
mkdir git && cd git
[COLOR=#333333][FONT=UbuntuRegular]Check out the repository:[/FONT][/COLOR]
git clone https://github.com/Bumblebee-Project/bumblebee-ui.git
cd bumblebee-ui
sudo ./INSTALL
[COLOR=#333333][FONT=UbuntuRegular]Go to Startup Applications and add bumblebee-indicator[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Now reboot.[/FONT][/COLOR]
```

Then I should be able to switch between grafics card or select what programs should run with Nvidia card.

What I would like to know is if when I'm using the integrated HD intel if the nvidia is completly turned off or not (I think I would like it to be this way, because if I don't need nvidia to run it should be turned off as well as vent turned off)

---

### Post by dannyboy79 on 2014-10-29
in almost every situation you'll want to be using the nvidia graphics card. may i ask why you want to use the built in intel one?

---

### Post by ricak on 2014-10-29
Sure you can!
you must be must more experienced than me as well, and that is why I created the post at this forum! :)

The logic I was trying to follow was that, the laptop has dedicated and integrated graphics.
There is also many similar laptops with same processor power and Intel HD graphics but without dedicated graphics.
So I thought that for "normal use" (mainly browsing and watching videos - streaming) the intel hd would be more than enough.
But for when I would like to play (for example Counter strike, Dota 2.... any game in general), I would use the nvidia.
This way, i think, I would be saving more battery.

Am I thinking wrong?
and why do you say I would be wanting to use nvidia in almost every situation?

thanks

---

### Post by ricak on 2014-10-30
Anyone?
Thank you

---

### Post by ricak on 2014-10-30
Also, and to add to my questions, when it comes to gaming does it matter what environment I use? like unity, gnome, or any other?

---

### Post by oldrocker99 on 2014-10-30
[http://jeffhoogland.blogspot.com/2013/02/comparison-of-linux-desktops-opengl.html](http://jeffhoogland.blogspot.com/2013/02/comparison-of-linux-desktops-opengl.html)

The bottom line is that all the desktops have pretty good OpenGL performance. The best performance is (unsurprisigly) LXDE and E17. KDE, when you disable effects for fullscreen windows (on the third tab of the Kwin control), is pretty good. In fact, although KDE does use more memory than other desktops, but not as much as Unity does:
[https://flexion.org/posts/2014-03-memory-consumption-of-linux-desktop-environments.html](https://flexion.org/posts/2014-03-memory-consumption-of-linux-desktop-environments.html)

The memory usage of various desktops is here:
| Desktop Environment  | Memory Used |
| ---------------------|--------------------:|
| Enlightenment 0.18.8 |        83.8 MiB |
| LXDE 0.5.5                |    87.0 MiB     |
| XFCE 4.10.2              |   110.0 MiB    |
| LXQt 0.7.0                |   113.0 MiB    |
| MATE 1.8.1               |   123.0 MiB    |
| Cinnamon 2.2.13      |   176.3 MiB    |
| GNOME3 3.12.2        |   245.3 MiB |
| KDE 4.13.1              |   302.6 MiB |
| Unity 7.2.0.14          |   312.5 MiB |
Source:
[https://flexion.org/posts/2014-03-memory-consumption-of-linux-desktop-environments.html](https://flexion.org/posts/2014-03-memory-consumption-of-linux-desktop-environments.html)

I personally use MATE because I like it the best (BTW, pronounced "mah-TAY," named for the Argentinian caffienated herb; MATE started development in Argentina, which is why its apps have Spanish names: Caja for Nautilus, Pluma for Gedit, etc.) MATE is a fork of the GNOME 2.32 that **used** to be the default desktop for Ubuntu, before GNOME started removing features from its feature set, and oldtimers such as I am, prefer it above other desktops. 

Note: MATE (currently) has high CPU usage for its Caja file manager, which I avoid by using Nautilus, which is the most full-featured GTK file manager, more so than Caja. Yes I know about KDE's Dolphin.

---

