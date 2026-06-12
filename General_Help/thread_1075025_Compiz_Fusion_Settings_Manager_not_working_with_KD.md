---
title: "Compiz Fusion Settings Manager not working with KDE 4.1 + Ubuntu 8.10"
date: 2009-02-19
forum: General Help
---

### Post by James78 on 2009-02-19
As mentioned in topic title, I cannot get my Compiz Settings Manager to work with KDE 4.1 + Ubuntu 8.10

I can start it and all that, but when I apply settings, they don't ever work, nor apply. It appears that KDE is able to make use of these Compiz settings in their own manager, and it works. No matter what I try, compiz --replace, etc etc, nothing EVER works. I use the Emerald theming manager right now, and that was hard enough to get it to work, however it works right now just like I want.

On a second note, while I was trying to find the problem, I uninstalled some programs related to KDE, when you click 'Desktops' in System Settings, I get a message "The shared library was not found. Library "kcm_kwindesktop" was not found." I would like to re-install the programs I uninstalled, to fix what problems I caused in KDE.

Please help me fix both these issues!! As a note, Compiz was working perfectly fine and normal before the upgrade to Ubuntu 8.10.

---

### Post by James78 on 2009-02-20
Bump..

---

### Post by Mercury_Alpha on 2009-02-20
KDE uses kwin instead of compiz. When KDE is running, compiz is disabled.

As for restoring deleted packages, you can re-install them with Synaptic. In Synaptic, go to File>History to access a database showing every package you've installed, reinstalled, or removed, in chronological order.

---

### Post by James78 on 2009-02-20
My window manager is actually using Compiz, and window decorator is Emerald. I made sure of this by using Fusion Icon and setting what programs were being used. I also used the console commands to make double sure of this, and it's correct. The same problem still exists.

---

### Post by trlkly on 2009-02-20
Were you using KDE 4.1 before you upgraded? I've found it to be quite buggy*, so it wouldn't surprise me that it doesn't interface with Compiz properly. I honestly don't think 4.1 is ready for prime time.

So anyways, compiz may not work properly with the new KDE. You might want to post on a KDE forum, or check their bug reports.

*It's so buggy, I'm still using Ubuntu 8.04.

---

### Post by James78 on 2009-02-20
Mm, ok thanks. And if I recall, I actually was not using KDE 4.1 before this. I'll be sure to go post in their forum.

---

### Post by James78 on 2009-02-20
Downgrading won't be fun.

---

### Post by trlkly on 2009-02-20
Well, I don't think you have to downgrade all of Ubuntu. I just had a Hardy backup, so when my Intrepid got messed up, I just restored my backup.

[This forum](http://ubuntuforums.org/showthread.php?t=963695) may be of benefit to you.

---

