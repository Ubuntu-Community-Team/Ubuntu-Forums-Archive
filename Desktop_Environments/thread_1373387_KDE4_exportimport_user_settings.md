---
title: "KDE4 export/import user settings"
date: 2010-01-05
forum: Desktop Environments
---

### Post by leon.hh on 2010-01-05
Hello everybody! Happy New Year... I'm here with another of my complicated problems.

The thing is that I've adapted KDE4 in an excellent way, but it was a lot of work, now I have the need of replicate those settings to many other systems.

Doing it by hand would be difficult, slow and it implies a very high chance of mistakes. What I've been looking for the last 4 days (without any luck) is a way to export an already configured KDE4 desktop to a file (or folder) and been able to import it later into a non-configured KDE4 desktop in order to make them identical.

It would be also desirable to make those settings default for every user created in the system, but if the last is not possible, I need at least the first.

Thank you

---

### Post by garryknight on 2010-01-05
Anything in /etc/skel gets copied into new users home directories. You should be able to set up a default .kde directory there.

---

### Post by leon.hh on 2010-01-06
I thought that long time ago, it was the first thing I did, but it's not so easy, when you copy your configured .kde folder to /etc/skel and create a new user, this .kde folder it's indeed copied to the home of the brand new created user, but at it's startup KDE4 starts the KDE Migration settings (like when you update from KDE3 to KDE4) and no matter what options you select, it'll die and restart to KDM.

So, the /etc/skel solutions does not solve my problem, at less not in the simple way you're posting

---

### Post by garryknight on 2010-01-06
Ok, sorry I couldn't help.

---

### Post by leon.hh on 2010-01-06
Don't worry, thanks anyway for your reply

---

### Post by leon.hh on 2010-01-07
SUCCESS!!!!

I finally found the way: First, locate the ```
.kde/share/config
``` and select the necesary files of your configured applications (you can copy them to a temporay folder), then it is necesary to edit them one by one in order to delete every user-specific information (like history of open files) and copy the edited files to ```
/usr/share/kde4/config
```

Finally fix the files permissions at /usr/share/kde4/config (owner root, permissions 644 for files and 755 for folders). That's it... Every newly created user will be created with the settings we want. Locating and editing the files one by one requieres a lot of work, but it totally worthed

---

### Post by garryknight on 2010-01-07
Glad you solved it. :)

---

### Post by Lampi on 2011-02-02
With KDE 4.4.5 the config files are supposed to be placed in /etc/kde4/config - files placed in there have precedence over the files in /usr/share/kde4/config. Like this you still have the original in case you mess sth up editing the file...

Does this also work for the files in ~/.kde/share/apps?

There is no Readme in /usr/share/kde4/apps that points to do so. I do have quite a few adjustments in apps as well like konsole profiles, kaffeine channel lists and so on.

Is is safe to strip those files from user specific entries and place them to /etc/kde4/apps, or do they have to be placed in /usr/share/kde4/apps?

---

