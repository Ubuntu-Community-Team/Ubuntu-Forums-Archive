---
title: "Fluxbox: Keyboard layout plugin needed!"
date: 2010-02-04
forum: Desktop Environments
---

### Post by vickoxy on 2010-02-04
Hi,
i am using linux mint fluxbox 8 RC 1. I need more keyboard layouts, but there is no applet/plugin that i can use. How can i get in fluxbox panel some applet and where should i setup desired keyboard layouts (in Ubuntu 8.04 i did it in xorg.conf but now i ca not find this file any more).

Thanks

---

### Post by vickoxy on 2010-02-04
Well, i change keyboard layouts often so i need some place where i can make this change quick (it would be the best in panel-as some applet in xfce/gnome). But i found one elegant solution. I added in menu this:

    [separator] (--------)
    [submenu] (Tastatur)
    [exec] (De) {setxkbmap de}
    [exec] (Hr) {setxkbmap hr}
    [exec] (Sr) {setxkbmap cs}
    [end]
    [separator] (--------)



So, it looks fluxbox nice, and it functions after every restart.

Still, if someone find some good applet i would be grateful.

Thanks

---

### Post by Odd-rationale on 2010-02-04
Have you tried fbxkb? I believe it is in the Karmic repos.

[http://fbxkb.sourceforge.net/index.html](http://fbxkb.sourceforge.net/index.html)

---

### Post by vickoxy on 2010-02-04
Well, i tried, but it doesn´t look very nice with those flags in fluxbox. And i do not know how to set only letters...

---

### Post by Odd-rationale on 2010-02-04
Well CrunchBang Linux (Ubuntu-based distro: [http://crunchbanglinux.org/](http://crunchbanglinux.org/)) has a nice keyboard switcher. I do not know what the name is, but you probably can find out.

You can see a screenshot of it here (the applet with "GB"):

[http://www.dedoimedo.com/images/computers_new_1/crunchbang-desktop.jpg](http://www.dedoimedo.com/images/computers_new_1/crunchbang-desktop.jpg)

Link to full review where image comes from:

[http://www.dedoimedo.com/computers/crunchbang.html](http://www.dedoimedo.com/computers/crunchbang.html)

Hope that helps!

---

