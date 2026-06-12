---
title: "App launched as root has a different style (gnome?)"
date: 2009-12-18
forum: Desktop Environments
---

### Post by kai.scorpio on 2009-12-18
I have an application (fwbackups) that I usually run as root for some extra functions. It functions fine, but running it as root changes the GUI. The buttons and icons changed, it looks very gnome-ish as root. Any ideas what I can do?

Running kubuntu 9.10, gnome themes are installed.

---

### Post by mac9416 on 2009-12-18
Howdy,

The GTK themes are configured per user. Look at this for how to set your root GTK theme: [http://tombuntu.com/index.php/2007/09/18/theme-applications-running-as-root-in-ubuntu/](http://tombuntu.com/index.php/2007/09/18/theme-applications-running-as-root-in-ubuntu/)

Good luck!

---

### Post by schnelle on 2009-12-18
Try this:

Install package "gtk-chtheme". Then press alt+f2 and type "kdesudo gtk-chtheme". Choose QtCurve style and press "apply".

This solved my problem with ugly theme when I run synaptic as root.

---

### Post by kai.scorpio on 2009-12-18
This looks good for gnome, but I'm on kubuntu, so can anybody give me the KDE version of these?

I don't have any of the directories (.themes, .icons) in my home dir or root home dir.

---

### Post by lovinglinux on 2009-12-18
> **kai.scorpio said:**
> This looks good for gnome, but I'm on kubuntu, so can anybody give me the KDE version of these?

I don't have any of the directories (.themes, .icons) in my home dir or root home dir.

Install [gtk-qt-engine](apt:gtk-qt-engine) and then do [this](http://ubuntuforums.org/showpost.php?p=8107813&postcount=17).

---

### Post by kai.scorpio on 2009-12-18
apt-get can't find gtk-qt-engine, it says it has been replaced by kcm-gtk, which is installed. And this means I don't have the directories mentioned there either.

Here's what's in my home dir:
```

.              Custom     .fontconfig  .gnome2_private  Music                .Skype                     .xine
..             .dasher    .fonts.conf  .gnupg           Pictures             .subversion                .xsession-errors
.adobe         .dbus      .fwbackups   .gtkrc-2.0-kde4  .pki                 .sudo_as_admin_successful
.bash_history  Desktop    .gconf       .gvfs            .profile             Templates
.bash_logout   .dmrc      .gconfd      .java            Public               .thumbnails
.bashrc        Documents  .gegl-0.0    .kde             .pulse               .update-manager-core
.cache         Downloads  .gimp-2.6    .local           .pulse-cookie        Videos
.config        .esd_auth  .gnome2      .macromedia      .recently-used.xbel  .Xauthority


```

---

### Post by lovinglinux on 2009-12-18
> **kai.scorpio said:**
> apt-get can't find gtk-qt-engine, it says it has been replaced by kcm-gtk, which is installed.

:oops: you are correct.

> **kai.scorpio said:**
> And this means I don't have the directories mentioned there either.

The file you need is **.gtkrc-2.0-kde4** rename it to **.gtkrc-2.0** and copy it to the root user folder.

```
cp ~/.gtkrc-2.0-kde4 ~/.gtkrc-2.0
sudo cp ~/.gtkrc-2.0 /root/.gtkrc-2.0
```

---

### Post by kai.scorpio on 2009-12-19
ah, whoops on my part too, somehow I didn't see that file. That's all fixed now.

Little related issue that's bugging me, somehow chromium has different mouse cursors (for resizing and such) than everything else, any ideas there?

---

