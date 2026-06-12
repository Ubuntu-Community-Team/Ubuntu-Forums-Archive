---
title: "nautilus single window? slow copy of samba shares"
date: 2005-01-01
forum: Desktop Environments
---

### Post by Golovko on 2005-01-01
I have several issues. If anyone could help, or give me some pointers on how to more accurately debug these it would be awesome:

1. (Simple I think). How to make nautilus stop opening a new window every time I open a folder?

2. Copying a directory from a samba share with nautilus is extremely slow. For example a 100 MB folder of mp3's, the initial time estimate is about 13 minutes, and when completed took about that much time. What could cause this? How could I go about debugging this behavior.

Gol

---

### Post by jeremy on 2005-01-01
In answer to your fist question;
Edit -> Preferences -> Behaviour, select 'Always open in browser windows'.

Can't help you with the other one, I'm afraid.

---

### Post by kral on 2005-01-01
look at the samba configuration (/etc/samba/smb.conf)

its maybe the anti-spoofing protection, that overslow the connection.

---

### Post by mark_lagace on 2005-01-07
> 2. Copying a directory from a samba share with nautilus is extremely slow. For example a 100 MB folder of mp3's, the initial time estimate is about 13 minutes, and when completed took about that much time. What could cause this? How could I go about debugging this behavior.

I found my samba access was extremely slow until I added my samba server to my /etc/hosts file (and made sure wins name resolution was disabled, but since the host file is higher up in the lookup order than wins is, that shouldn't matter).

---

