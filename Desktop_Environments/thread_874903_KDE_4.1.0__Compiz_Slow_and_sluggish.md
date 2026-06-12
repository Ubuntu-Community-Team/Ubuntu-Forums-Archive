---
title: "KDE 4.1.0 / Compiz Slow and sluggish"
date: 2008-07-30
forum: Desktop Environments
---

### Post by Syirrus on 2008-07-30
I'm running ubuntu 8.04.1 and decided to install KDE 4.1.0 using the method here: [http://news.softpedia.com/news/How-To-Install-KDE-4-1-On-Ubuntu-8-04-91034.shtml](http://news.softpedia.com/news/How-To-Install-KDE-4-1-On-Ubuntu-8-04-91034.shtml)

Everything went according to plan and now i am running KDE 4.1.0. I enabled compiz fusion but it seems sluggish when I compare it to Gnome.  I made sure that the built in KDE desktop effects were disabled too.  Whenever I minimize windows or rotate the cube its very choppy.  I'm running a Q6600 with an 8800GTX.  Any suggestions?

---

### Post by Zorael on 2008-08-02
Make sure that you have the same settings in ccsm; chances are your Compiz profile is saved with a gconf backend (check in Preferences in ccsm), whereas Compiz in KDE prefers its own backend. If they differ, export your profile in Gnome and then import it in KDE.

The best solution would be to switch to flat-file frontend, making KDE and Gnome read the same settings file and keeping any changes you make in one environment carry over to the other. Just make sure that you export your profile before changing frontend, or you may lose your settings. Again, Preferences in ccsm.

If you're already using flat-file, this whole post is irrelevant and you should just ignore me.

---

### Post by benerivo on 2008-08-02
Also check [this]("http://techbase.kde.org/User:Lemma/KDE4-NVIDIA"). I think it only relates to how kde's inbuilt effects perform with nvidia 8xxx or 9xxx cards, rather than how compiz performs, but it is certainly worth a look.

---

### Post by chiccoch on 2008-08-28
OK, i'am using Gnome, not KDE, but this might stil help:

I've been locking around for a solution concerning the slow performance of compiz with nvidia cards. I tried all kinds of scripts, xorg options and lots of other stuff.

Finally I found a simple solution. Installing "fusion-icon", starting it, then right-clicking on it and finally activating "Compiz Options"-> "Loose Binding" and "Indirect Rendering", brougth my system back to normal.

I now have plenty of performance, even with 10 movies playing and 30 firefox windows open...

---

