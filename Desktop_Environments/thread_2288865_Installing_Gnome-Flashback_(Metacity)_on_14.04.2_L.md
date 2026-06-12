---
title: "Installing Gnome-Flashback (Metacity) on 14.04.2 LTS"
date: 2015-07-30
forum: Desktop Environments
---

### Post by c_xy on 2015-07-30
Hello,

We are using Ubuntu 14.04.2 LTS server. We wanted to install Gnome-flashback since most of us are familiar with that desktop environment.

Is there a way to **ONLY **Metacity with our Compiz?

In the past we installed with a two step process:

```
sudo apt-get install ubuntu-desktop
```

then

```
sudo apt-get install gnome-session-flashback
```

However, we don't want unity or compiz. Just metacity installed. Is there a particular command that would only install Metacity **without **Compiz or Unity. Or does flashback have dependencies connected with Unity where Unity has to be installed?

Any help is greatly appreciated.

c

---

### Post by grahammechanical on 2015-07-30
Metacity does not depend on Compiz. Unity is a Compiz plugin so Unity depends on Compiz. Metacity is a window manager. Compiz is a window manager/compositor. We can have both installed but we will only use one or the other after the login screen.

If you do not install a desktop environment, then I doubt there will be very much for Metacity to manage. And Ubuntu Desktop will bring in Compiz and Unity. You may be better off investigating ubuntu-mate-desktop. I do not think that you will get Compiz or Unity with the Ubuntu Mate desktop.

With Ubuntu Mate desktop environment you may not need Gnome Flashback at all.

Regards.

---

### Post by deadflowr on 2015-07-30
You should be able to get just the fallback session, by only running
```
sudo apt-get install gnome-panel
```
and ignoring the ubuntu-desktop package entirely.
Then install any extra packages you want later.

gnome-panel is gnome-fallback, and only includes the metacity window manager and not compiz, and therefor no unity either.
If you installed the ubuntu-desktop package then you'd be installing unity and therefor the compiz packages, which the fallback session would be able to use.

(Though to be fair, a few packages will have unity names in them, but that will be all. No need to worry about those.
(They are packages like unity-control-center, which is Ubuntu's re-tooled version of the gnome-control-center))

As if any of that makes sense...

---

### Post by v3.xx on 2015-07-30
You can install flashback/metacity without the ubuntu-desktop and compiz.

```
sudo apt-get install --no-install-recommends gnome-session-flashback
```

This will require using either startx or a display manager to login.

---

### Post by claracc on 2015-07-31
Here, [http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264), you have a very good and self explanatory thread about the installation of gnome flasback desktop and some workarounds for new problems.

---

### Post by c_xy on 2015-07-31
Thanks guys for the suggestions.

It looks like the installation may more of a work around than I anticipated. 

I'll take these into consideration and explore the different options.

Thanks again.  

c

---

