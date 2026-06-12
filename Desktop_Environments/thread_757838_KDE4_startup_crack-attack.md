---
title: "KDE4 startup crack-attack"
date: 2008-04-17
forum: Desktop Environments
---

### Post by immerohnegott on 2008-04-17
just installed the latest KDE4 in the ppa servers on my laptop (running Gutsy/gnome), and when I load it, it inexplicably runs all entries listed in my startup scripts for gnome and fluxbox (wouldn't be a problem if these hadn't been bloody *deactivated*). I tried putting these apps in the "exclude from sessions" dialog in System Settings>Session Manager under K4, to no avail. Looked through my ~/.kde4 folder for a config script, found nothing. 

Any ideas on this?

---

### Post by Tomatz on 2008-05-22
BUMP!


Same problem here.

---

### Post by Tomatz on 2008-05-22
Strange problem :confused:


Anyone???

---

### Post by sagematt on 2008-06-07
Confirmed in KDE 4.1 Beta 1. It's really getting on my nerves.

---

### Post by Tomatz on 2008-06-07
I have replicated the same problem. It is because you are using gdm to login to kde.

Either switch to kdm or create a script in /usr/bin to kill your gnome autostarted apps (in kde). 

E.g:

```
killall fusion-icon | killall crack-attack | killall the-list-goes-on
```

Then just symlink it to your kde **.autostart** folder. It worked for me :)


If you need any help just post back.

---

