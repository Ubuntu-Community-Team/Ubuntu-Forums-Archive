---
title: "Switching Desktop Managers"
date: 2006-06-21
forum: Desktop Environments
---

### Post by mhinton539 on 2006-06-21
I currently have Ubuntu 6.06 installed on my (ancient) iBook. I've installed quite a bit of KDE (the KDevelop IDE, KDE libraries, bunches of KDE apps), and would like to be able to startup into either KDE or Gnome. What packages do I need, and what files need to be changed in order to start KDE or Gnome? [I didn't see anything on this in the user docs; if there is something there, please point me in the right direction!]

Thanks,
Mark

---

### Post by fritz_monroe on 2006-06-21
You can bring up Synaptic Package Manager and install KDE.  THis should install all the rest of what's required for KDE.  Then when you get to your logon screen, click the sessions button to pick which desktop manager you want to use.

---

### Post by aysiu on 2006-06-21
```
sudo aptitude update
sudo aptitude install kde-core
``` or you could do *kubuntu-desktop* instead of *kde-core*. Read more here: [http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)

---

### Post by lindyslack on 2006-06-21
I am not a big KDE fan but I do like my fluxbox! :D 

So I sudo apt-get install fluxbox and then when I log out I can use the sessions option at the login prompt to choose fluxbox... I use flux on this any time I don't want gnome sucking my resources... Not that it's all that bad... Still runs better then windoze but this thing just flys with fluxbox running... I also use fluxbox on an HP Omni-book w/ a PII 233Mhz with FreeBSD and it runs great too!

---

