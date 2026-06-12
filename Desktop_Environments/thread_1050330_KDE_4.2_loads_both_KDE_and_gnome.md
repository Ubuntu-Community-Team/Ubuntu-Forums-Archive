---
title: "KDE 4.2 loads both KDE and gnome"
date: 2009-01-25
forum: Desktop Environments
---

### Post by theCroc on 2009-01-25
For some strange reason KDE 4.2 RC1 loads the gnome-panel and compiz.

I use ubuntu 8.10 (Running gnome with no issues) and decided to try out KDE 4.2. So I added the repo and installed the package kubuntu-desktop. 

When I log into the KDE session the kde desktop loads fine. Immediately after its done loading kde it starts up compiz and lads gnome on top of it. The results is metacity borders and compiz behaviour with gnome-panels on top of the kde panels. The gnome session is fine and does not display any odd behavior.

How can I get the KDE session to load only KDE 4.2 with Kwin? Where should I look?

---

### Post by theCroc on 2009-01-26
Anyone else having this problem? Where should I start looking at how the sessions load? I don't know enough about the config-files myself.

---

### Post by h4p0 on 2009-02-07
Same problem here....Very annoying. :@

---

### Post by h4p0 on 2009-02-07
Well, I solved the problem:
that seems to be a gnome bug, not a kde bug.

[http://bugs.kde.org/show_bug.cgi?id=163582](http://bugs.kde.org/show_bug.cgi?id=163582)

try this:


```

sudo -s

cd /etc/xdg/autostart

for file in `ls`; do echo "OnlyShowIn=GNOME" >> $file ; done

```

of course you can add the line "OnlyShowIn=GNOME" only in files you need.
:popcorn:
gnome-do.desktop
every_other_autostarting_app.desktop.

That simple workaround should go.
The situation seem not change for screenlets daemon cause it hasn't a .desktop to call...

---

