---
title: "KDE4 Crashes when booting (GRR)"
date: 2008-06-03
forum: Desktop Environments
---

### Post by Klonoa on 2008-06-03
When I try to start a session using KDE4 it loads fine, then out of the blue it crashes as if i  pressed Ctrl Alt Backspace, just out of nowhere CRASH. I am using Gnome but I perfer KDE, can someone help me? Yes I am in Ubuntu.

---

### Post by ajgreeny on 2008-06-03
Probably best to just ignore KDE4 until it becomes stable and use 3.5.9 or whatever the older version is.

---

### Post by Klonoa on 2008-06-03
Ahh well than I will stick with Gnome, I like it better than KDE 3.5, just wanted to give 4 a try.

---

### Post by F4l3 on 2008-06-04
do you have KDE4.0.0 or KDE4.0.4? If you have KDE4.0.0, go to [http://kubuntu.org](http://kubuntu.org) and there there are all the instruction to put 4.0.4 (and in a few days even 4.1b1) :). Good luck

---

### Post by Klonoa on 2008-06-04
I am very new to Ubuntu and I have no idea how to determine which KDE4 version I have. Today I just went to terminal and did the apt-get KDE4, and I could also not find the KDE download on Kubuntu, I could only find the download of the Kubuntu ISO.

---

### Post by F4l3 on 2008-06-04
> **Klonoa said:**
> I am very new to Ubuntu and I have no idea how to determine which KDE4 version I have. Today I just went to terminal and did the apt-get KDE4, and I could also not find the KDE download on Kubuntu, I could only find the download of the Kubuntu ISO.
ok, than you have KDE4.0.0.
I suggest you to follow this guide: [http://kubuntu.org/announcements/kde-4.0.4.php](http://kubuntu.org/announcements/kde-4.0.4.php)
Good luck ;)

---

### Post by Klonoa on 2008-06-04
I would not exactly call that a guide, it did nto really instruct me to do anything, I don't necessarily want to install the whole Kubuntu. I just want KDE4.

---

### Post by F4l3 on 2008-06-04
there is the guide. Here the main point:

The packages are in hardy-backports, available from Adept Manager when you choose Unsupported Updates from the Updates tab of Manage Repositories, kubuntu-kde4-desktop and do a full upgrade.

install kubuntu-kde4-desktop is not meaning install kubuntu, but all the kde4 packages ;)

---

### Post by Klonoa on 2008-06-04
Ok now I installed the Kubuntu KDE4 Desktop, and I restarted and tried to run a KDE 4 session, it started up displayed the desktop for 5 seconds played an error sound, and crashed back to login.

---

### Post by ChameleonDave on 2008-06-04
> **Klonoa said:**
> Ok now I installed the Kubuntu KDE4 Desktop, and I restarted and tried to run a KDE 4 session, it started up displayed the desktop for 5 seconds played an error sound, and crashed back to login.

Have you tried deleting your configuration files?

```
rm -fr ~/.kde4
```

---

### Post by F4l3 on 2008-06-04
> **Klonoa said:**
> Ok now I installed the Kubuntu KDE4 Desktop, and I restarted and tried to run a KDE 4 session, it started up displayed the desktop for 5 seconds played an error sound, and crashed back to login.
It will update the KDE4 packages that you actually have

---

### Post by Klonoa on 2008-06-04
putting that command into terminal did nothing, and it still says KDE 4.0 at the startup of KDE 4.

---

### Post by ChameleonDave on 2008-06-04
> **Klonoa said:**
> it still says KDE 4.0 at the startup of KDE 4.

I suspect that that is just a pretty splash screen image on which someone put "4.0".  It will continue to say that until it is replaced.  I doubt it actually depends on the real version number.

---

### Post by ajgreeny on 2008-06-04
If you can actually get kde running, open an application and go to Help>>About kde and there you will see, or at least you used to in older versions, which version you are running. It may be that kde4 has not quite caught up with that yet, but it's worth trying.

---

### Post by Klonoa on 2008-06-04
After I updated and everything, it did the usual stuff, opened played an error noise and crashed. I opened Kate in GNOME and clicked on about KDE and it said version 4.0.3.

---

