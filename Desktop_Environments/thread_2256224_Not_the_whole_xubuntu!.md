---
title: "Not the whole xubuntu!"
date: 2014-12-10
forum: Desktop Environments
---

### Post by jevon2 on 2014-12-10
Hi,

I installed 12.04 unity and due to various problems, and performance (most likey due to being in a VM) I installed xubuntu-desktop. This worked fine. I like xubuntu.

After a regular 12.04 system update (a few weeks ago) I lost some of my xubuntu features:

1) Desktop wallpaper is the purple "Unity" wallpaper - desktop settings indicate I have my original xubuntu wallpaper set (the blue one with birds)
2) No standard desktop icons - desktop settings says they are enabled

Otherwise, I see xubuntu menu, terminal, windows, and splash screens during login/logoff.

Last time I fiddled I broke everything. Should I do a reinstall of xubuntu-desktop (xfce)? and how? Suggestions.

Thanks,
Jevon

---

### Post by ibjsb4 on 2014-12-11
You say installed Xubuntu-desktop.  Thats the package that could be used to install Xu to a Unity install and suggest that you added X to U.  If thats the case, I suggest a fresh install of Xu only.

You could also try yet another desktop.  'Fallback'  It looks like Xu and uses metacity instead of compiz to speed things up.
```
sudo apt-get install gnome-panel
```

---

### Post by egeezer on 2014-12-11
You could also try another way to get a Xubuntu-like version of Ubuntu without have to install Abiword along with LibreOffice (I confess, I HATE Abiword!).  Instead of

```
sudo apt-get install xubuntu-desktop
```

use

```
sudo apt-get install xfce4 xcfe4-goodies
```

Then you will be running Ubuntu with all the Xfce appearance options.  By the way, you might want to install Xfce 4.10 via a PPA, since Ubu 12.04 came with Xfce 4.8.

---

### Post by jevon2 on 2014-12-11
Thanks for your suggestions. I got my classic xubuntu desktop back (with icons).

I followed the instructions here [http://askubuntu.com/questions/344089/how-to-install-xfce-4-12-on-ubuntu-12-04](http://askubuntu.com/questions/344089/how-to-install-xfce-4-12-on-ubuntu-12-04) to upgrade xfce.

However, I strongly suspect the apt-get dist-upgrade did the the trick (apt-get upgrade is restricted in what it can do). It was a routine software update that caused the original problem.

Thanks,
Jevon

---

