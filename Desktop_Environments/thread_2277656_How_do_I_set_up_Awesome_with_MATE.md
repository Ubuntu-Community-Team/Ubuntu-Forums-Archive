---
title: "How do I set up Awesome with MATE?"
date: 2015-05-10
forum: Desktop Environments
---

### Post by Nickolai_Leschov on 2015-05-10
There's a tutorial called [Quickly Setting up Awesome with Gnome]("https://www.google.com/search?q=Quickly+Setting+up+Awesome+with+Gnome&ie=utf-8&oe=utf-8")  describing the process of setting up [Awesome]("http://awesome.naquadah.org/") in such a way as to retain  some features and advantages of GNOME. Since MATE is a fork of GNOME 2,  I thought I could apply the steps described for GNOME <3, namely:
```
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false
```
and
```
gconftool-2 --type string --set /desktop/gnome/applications/window_manager/current /usr/bin/awesome
```
or
```
gconftool-2 --type string --set /desktop/gnome/applications/window_manager/current /usr/bin/awesome
```
then write
```
[Desktop Entry]
Version=1.0
Type=Application
Name=Awesome
Comment=The awesome launcher!
TryExec=awesome
Exec=awesome

```
to ~/.local/share/applications/awesome.desktop. Still there was no effect. Where should I start looking to figure out what am I doing wrong?

---

### Post by deadflowr on 2015-05-10
Mate uses different names, such as caja instead of nautilus.
And I do not think mate uses any references to gnome...
They renamed quite a bit to avoid conflicts and such.

---

### Post by Nickolai_Leschov on 2015-05-10
So, the GNOME tutorial *shouldn't* work verbatim. Ok, now to figure out what should work...
I have already asked on [FONT=courier new]mate-dev[/FONT] and [FONT=courier new]awesome[/FONT] mailing lists, but got no questions so far, so I decided to try my luck here.

---

### Post by v3.xx on 2015-05-10
Yep, those commands won't work.  So I took a look and didn't hit on anything good.  I would say that your in uncharted waters.

The little bit of info I did find suggest that names can be changed, but other processes behind the scene are a problem.

---

