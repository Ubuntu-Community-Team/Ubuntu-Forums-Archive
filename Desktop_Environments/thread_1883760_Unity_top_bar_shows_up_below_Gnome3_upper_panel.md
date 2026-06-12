---
title: "Unity top bar shows up below Gnome3 upper panel"
date: 2011-11-19
forum: Desktop Environments
---

### Post by odiseo77 on 2011-11-19
Hello people, this is a minor issue, but still annoys me a little bit. I'm using Ubuntu 11.10 and I use mainly Gnome3. The problem is the Unity top bar is showing up below the Gnome 3 upper panel, as you can see in the image (the Gnome bar is transparent, so I can see the Unity bar below it).

BTW, I switched from lightdm to GDM thinking it could solve the problem, but it didn't work. Is there any way to solve this issue?

Thanks in advance.

---

### Post by Copper Bezel on 2011-11-19
That's not the Unity bar - it's drawn by Nautilus. (I thought this issue was fixed, though. Odd.) It'll disappear if you turn off desktop icons in gnome-tweak-tool ("Have file manager manage the desktop" in Desktop options.)

Edit: I guess it *is* related to Unity. The other fix, [_via WebUpD8_]("http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html"), is to remove the global menu packages:

```
sudo apt-get remove appmenu-gtk3 appmenu-gtk appmenu-qt
```

---

### Post by odiseo77 on 2011-11-19
You are right, it was Nautilus (since I haven't used Unity too much, I thought it was the same bar). I had not applied upgrades since I installed Ubuntu, because I use mainly Debian (I happened to boot Ubuntu a while ago and found the two bars overlapped above). I already applied the upgrades and the problem is gone now, even with the "Have file manager manage the desktop" option checked. Thanks for your help!

---

### Post by markbl on 2011-11-19
The problem with the solution quoted above is that it disables global menus in Unity also. I think a better fix is to put those packages back and then just type the following which fixes global menu problems in gnome-shell but does not affect Unity.
```

echo '[ "$DESKTOP_SESSION" != "ubuntu" ] && unset UBUNTU_MENUPROXY' | sudo tee /etc/X11/Xsession.d/81ubuntu-menu-proxy

```

---

### Post by odiseo77 on 2011-11-19
Thanks, markbl, but I didn't have to remove the packages mentioned by Copper Bezel because the problem got fixed just by upgrading the system (I only had upgraded it right after installing 11.10, when it was launched in october). It's fine now. Thanks for the suggestion, anyway!

---

### Post by markbl on 2011-11-19
That fix I suggest also fixes other Unity global menu bugs which affect gnome-shell though. E.g. I keep my system up to date so I just disabled that fix and tried to turn off the menubar in gnome-terminal but I find that the menubar keeps re-appearing without the fix. There are other apps affected in a similar way.

---

### Post by gclayton on 2012-02-24
THANK YOU!!!!! I have been chasing this for a week now. Your input was very helpful to me. Especially Copper Bezel. I can't stand Unity anyway so your fix was perfect for me.

---

