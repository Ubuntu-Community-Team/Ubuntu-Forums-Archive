---
title: "Global Menu in Maverick?"
date: 2010-10-13
forum: Desktop Environments
---

### Post by devondashla on 2010-10-13
I absolutely love the Gnome Panel Applet "Global Menu".

[https://launchpad.net/~globalmenu-team/+archive/ppa](https://launchpad.net/~globalmenu-team/+archive/ppa)

The problem is, I am unsuccessful in installing it on Maverick. It worked beautifully in Lucid. I add the PPA, but the package gnome-globalmenu is not in the repositories after I update the sources. Also, I am having problems installing it from source. Can anyone help me with this, or give me an alternative?

---

### Post by kerry_s on 2010-10-13
try "indicator-applet-appmenu" works just like global menu, you need to log out & back in after you add it.

---

### Post by devondashla on 2010-10-13
um...I'm not a big fan of your suggestion. It's okay, serves the purpose, but I just like the quality of Global Menu better.

---

### Post by sgosnell on 2010-10-14
You should be able to enable the Lucid repositories, install the package, then disable them again.

---

### Post by fimfree on 2010-10-14
> **devondashla said:**
> I absolutely love the Gnome Panel Applet "Global Menu".

[https://launchpad.net/~globalmenu-team/+archive/ppa](https://launchpad.net/~globalmenu-team/+archive/ppa)

The problem is, I am unsuccessful in installing it on Maverick. It worked beautifully in Lucid. I add the PPA, but the package gnome-globalmenu is not in the repositories after I update the sources. Also, I am having problems installing it from source. Can anyone help me with this, or give me an alternative?

You can use the appmenu the new globalmenu, Ubuntu made, you can install it by this command

```
sudo apt-get install appmenu-gtk indicator-appmenu indicator-applet-appmenu
```

For the gnome globalmenu, maybe the repository is not ready yet for Maverick.

---

### Post by devondashla on 2010-10-14
> **fimfree said:**
> You can use the appmenu the new globalmenu, Ubuntu made, you can install it by this command

```
sudo apt-get install appmenu-gtk indicator-appmenu indicator-applet-appmenu
```For the gnome globalmenu, maybe the repository is not ready yet for Maverick.

We already discussed that in earlier posts. Thank you, though.

---

### Post by Heero_Yuy_X on 2010-10-14
The Indicator AppMenu is broken too !! so it doesn't even compensate some of Global Menu's greatness ! :(

---

### Post by miesogeno on 2010-10-15
the indicator-applet-appmenu has a memory leak.

it started gathering memory until I had to restart it.
also, I think it also made nautilus get a memory leak.

since I removed it everything is fine. except that... i dont get to have the menus on the top panel. witch really irritates me, since I got used to them in lucid.

I also tried to get the globalmenu again for maverick, but with the same result as yours.

does anyone have an alternative solution?

---

### Post by sgosnell on 2010-10-15
Have you tried installing global menu from the .deb files?  I downloaded them from the ppa directly and installed with gdebi, without any problem other than the necessity for installing the subordinate debs before installing the main one.

---

### Post by miesogeno on 2010-10-15
well, thank you. i just tried that and it's working.

system monitor now shows 5,3 MB of Globalmenu memory usage.
indicator-applet-appmenu went up to 200 MB, before I killed its process.

thanks!

---

### Post by &#968;&#955;&#949;&#960;&#964;&#959; on 2010-10-27
> **sgosnell said:**
> Have you tried installing global menu from the .deb files?  I downloaded them from the ppa directly and installed with gdebi, without any problem other than the necessity for installing the subordinate debs before installing the main one.which packages have you install because i can't do it...

---

### Post by sgosnell on 2010-10-27
[https://launchpad.net/~globalmenu-team/+archive/ppa/+files/libgnomenu0-2_0.7.9-0ubuntu1%7Eppa1%7Elucid2_i386.deb](https://launchpad.net/~globalmenu-team/+archive/ppa/+files/libgnomenu0-2_0.7.9-0ubuntu1%7Eppa1%7Elucid2_i386.deb)

[https://launchpad.net/~globalmenu-team/+archive/ppa/+files/gnome-globalmenu_0.7.9-0ubuntu1%7Eppa1%7Elucid2_all.deb](https://launchpad.net/~globalmenu-team/+archive/ppa/+files/gnome-globalmenu_0.7.9-0ubuntu1%7Eppa1%7Elucid2_all.deb)

[https://launchpad.net/~globalmenu-team/+archive/ppa/+files/gnome-globalmenu-common_0.7.9-0ubuntu1%7Eppa1%7Elucid2_all.deb](https://launchpad.net/~globalmenu-team/+archive/ppa/+files/gnome-globalmenu-common_0.7.9-0ubuntu1%7Eppa1%7Elucid2_all.deb)

[https://launchpad.net/~globalmenu-team/+archive/ppa/+files/gnome-applet-globalmenu_0.7.9-0ubuntu1%7Eppa1%7Elucid2_i386.deb](https://launchpad.net/~globalmenu-team/+archive/ppa/+files/gnome-applet-globalmenu_0.7.9-0ubuntu1%7Eppa1%7Elucid2_i386.deb)

---

### Post by &#968;&#955;&#949;&#960;&#964;&#959; on 2010-10-27
> **sgosnell said:**
> [https://launchpad.net/~globalmenu-team/+archive/ppa/+files/libgnomenu0-2_0.7.9-0ubuntu1%7Eppa1%7Elucid2_i386.deb](https://launchpad.net/~globalmenu-team/+archive/ppa/+files/libgnomenu0-2_0.7.9-0ubuntu1%7Eppa1%7Elucid2_i386.deb)

[https://launchpad.net/~globalmenu-team/+archive/ppa/+files/gnome-globalmenu_0.7.9-0ubuntu1%7Eppa1%7Elucid2_all.deb](https://launchpad.net/~globalmenu-team/+archive/ppa/+files/gnome-globalmenu_0.7.9-0ubuntu1%7Eppa1%7Elucid2_all.deb)

[https://launchpad.net/~globalmenu-team/+archive/ppa/+files/gnome-globalmenu-common_0.7.9-0ubuntu1%7Eppa1%7Elucid2_all.deb](https://launchpad.net/~globalmenu-team/+archive/ppa/+files/gnome-globalmenu-common_0.7.9-0ubuntu1%7Eppa1%7Elucid2_all.deb)

[https://launchpad.net/~globalmenu-team/+archive/ppa/+files/gnome-applet-globalmenu_0.7.9-0ubuntu1%7Eppa1%7Elucid2_i386.deb](https://launchpad.net/~globalmenu-team/+archive/ppa/+files/gnome-applet-globalmenu_0.7.9-0ubuntu1%7Eppa1%7Elucid2_i386.deb)thank you....
its working perfect....

---

