---
title: "KDE Tooltips in Gnome unreadable (black on black)"
date: 2010-09-23
forum: Desktop Environments
---

### Post by brianschimmel on 2010-09-23
Hi there,

I'm using Ununtu 10.4 with Gnome, and recently installed KDE (KDE 4.4.92 (KDE 4.5 RC2)) on top so that I can choose between KDE and Gnome at each login. 

When I log into an KDE session, everything works just fine, but often I use KDE applications (like Okular and KDevelop) in my Gnome session. In Gnome, I'm using the dark default theme that came with Ubuntu 10.4, which features black tooltip boxes with white font. In KDE-Applications I get black tooltip boxes with dark-gray font. It is completely impossible to read them, the text is so dark that I can hardly see that there is text at all.

Has anyone an idea of how to fix this, possibly without breaking other things (like using Gnome-Apps in a KDE-Session, etc)?

Also, I'm wondering if this should have worked from the start, that is, if this issue is worth opening a bug report.

thanks in advance,
Brian

---

### Post by eltama on 2010-09-23
I'm having the same problem but with 10.10 beta (Maverick), in 10.04 it used to work fine.

---

### Post by eltama on 2010-09-23
I've solved it. It seems to be another incarnation of this bug [https://bugs.launchpad.net/ubuntu/+source/gtk2-engines/+bug/144968]("https://bugs.launchpad.net/ubuntu/+source/gtk2-engines/+bug/144968"), and it's duplicate [https://bugs.launchpad.net/ubuntu/+bug/141254]("https://bugs.launchpad.net/ubuntu/+bug/141254")

Basically what you have to do is to change the background of the tooltip on the theme, however the problem is that it looks OK, black background and white fonts, but for some reason it was not working.

To fix it go to System > Preferences > Appearance > Theme, click on Customize..., go to Colors click on the button for the background of Tooltips and choose a new background, it could be black again.

What I still don't like is that the menu entries that are not enabled are also very difficult to read on both GTK and Qt applications. I don't know how to change this.

---

### Post by brianschimmel on 2010-09-23
Thank you, that did the trick for me. Changed the background color from black to black and now I get white text.

---

### Post by eltama on 2010-09-24
> **brianschimmel said:**
> Thank you, that did the trick for me. Changed the background color from black to black and now I get white text.

Great!

---

### Post by bonzi on 2010-09-28
Thanks eltama. Worked for me too.

---

### Post by aybesea on 2010-11-09
This works for me too, but it resets back to dark grey on black as soon as I reboot (i.e. it is not a sticky setting). Anyone?

---

### Post by eltama on 2010-11-30
That's true, for me it resets even if I close the KDE program and I open it again.
I don't know of any permanent solution.

---

### Post by kaeptnbb on 2010-12-15
> **eltama said:**
> That's true, for me it resets even if I close the KDE program and I open it again.
I don't know of any permanent solution.
Use
```
sudo apt-get install systemsettings
```.
Now you can use systemsettings to configure tooltip bg and font color for KDE applications.

---

### Post by victorhugo289 on 2011-02-04
> **kaeptnbb said:**
> Use
```
sudo apt-get install systemsettings
```.
Now you can use systemsettings to configure tooltip bg and font color for KDE applications.

You guys just solved one little problem I had, Hurray!

---

### Post by makushimu on 2011-08-15
Thank you, this thread really helped!

---

### Post by ub-khalid on 2011-10-05
> **kaeptnbb said:**
> Use
```
sudo apt-get install systemsettings
```.
Now you can use systemsettings to configure tooltip bg and font color for KDE applications.


Thanks a lot, I'll see

---

### Post by ub-khalid on 2011-10-05
Dear [B]kaeptnbb
It haven't changed anything!
[/B]

---

