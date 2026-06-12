---
title: "[SOLVED] XFCE + Beryl = Tiny Workspace Switcher"
date: 2007-04-19
forum: Desktop Effects &amp; Customization
---

### Post by notwen on 2007-04-19
> I just did a fresh install of Xubuntu Fiesty herd5.  I then proceeded to install Beryl w/o a hitch.  I've been searching the forums, but haven't found my exact situation.  My workspace switcher on my panel is extremely small. (screenshot [here]("http://www.notwen.org/img/uf_xubuntu01.png"))  Any recommendations on getting my workspace switcher back to it's normal size? Thanks. =]

Haven't gotten any responses in Desktop Environments, so I'll try here. =p  Any info at all would be appreciated. Thanks

---

### Post by kariopto on 2007-04-20
*bump*
I have the exact same problem.

---

### Post by notwen on 2007-04-21
Glad to hear I'm not the only one w/ this issue.  If no solution comes up I'll be installing Fluxbuntu when it's Feisty based release comes out.   Let's keep our fingers crossed. =x

---

### Post by Bapman on 2007-05-02
Same problem too ! Someone doesn't actually has this problem ?

Also, I have another one with Beryl+XFCE (but it happened also on GNOME) : when a window is maximized and that I shut down the window, when I open the window again, it won't switch back to normal size if I push on the right button (it is always at its maximum size) !

---

### Post by livesys on 2007-05-02
This is a known problem with Xfce 4.4.0.

The newer Xfce 4.4.1 fixes this problem:

From [http://www.xfce.org/documentation/changelogs/4.4.1](http://www.xfce.org/documentation/changelogs/4.4.1)

** "Fix aspect ratio of the pager when using viewports, required for window managers such as Beryl that use multiple viewports within one single workspace."**


However, xfce 4.4.1 is not in the ubuntu repo.  If anybody see a .deb for xfce 4.4.1, please post link.

---

### Post by kariopto on 2007-05-03
Does anyone know if xfce-4.4.1 will be in the repos soon? Because I don't want to download and compile only to find it to be in the repos a few weeks later.
BTW, thanks for replying livesys.

---

### Post by Bapman on 2007-05-03
Thx livesys ! :D

I tried to compile the last version with the graphical installer. I satisfy all the dependancies according to it but when I compile, I get this error :
```
make[2]: quittant le répertoire « /tmp/selfgz8388/xfce-mcs-manager/doc »
Making all in po
make[2]: entrant dans le répertoire « /tmp/selfgz8388/xfce-mcs-manager/po »
file=`echo ar | sed 's,.*/,,'`.gmo \
	  && rm -f $file &&  -o $file ar.po
/bin/sh: -o: not found
make[2]: *** [ar.gmo] Erreur 127
make[2]: quittant le répertoire « /tmp/selfgz8388/xfce-mcs-manager/po »
make[1]: *** [all-recursive] Erreur 1
make[1]: quittant le répertoire « /tmp/selfgz8388/xfce-mcs-manager »
make: *** [all] Erreur 2
```

---

### Post by livesys on 2007-05-06
Look what I found in Gutsy repo :)

[http://packages.ubuntulinux.org/gutsy/x11/xfce4](http://packages.ubuntulinux.org/gutsy/x11/xfce4)

---

### Post by kariopto on 2007-05-06
All right!  :)

---

### Post by Bapman on 2007-05-07
Thanks a lot ;)

---

