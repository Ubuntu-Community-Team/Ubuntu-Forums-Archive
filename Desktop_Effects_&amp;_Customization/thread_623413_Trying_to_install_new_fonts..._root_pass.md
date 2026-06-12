---
title: "Trying to install new fonts... root pass??"
date: 2007-11-25
forum: Desktop Effects &amp; Customization
---

### Post by TV-VCR on 2007-11-25
All I wanted to do was install some fonts for system wide use. It's supposed to be easy yes? NO.

To use the "su" command, I need a retarted "root password". Ok I thought, I'd just try my own password. NO!!! It need the root password!

I have never set a root password. I have tried everything, from just pressing enter to typing "default". During installation it never asked me for a root pass.

How do I resolve this? :confused:

---

### Post by mjskia1 on 2007-11-25
AFAIK, Ubuntu disables the root password by default.  It uses the "sudo" command, which is set up to allow a regular user (the one you created when you installed) to perform superuser commands.

Instructions you'll find for other Linux distributions will often ask you to change to root using the su command.  In Ubuntu, instead of changing to root with su, type "sudo" before the command you want to run as the superuser.  Then give your user password.

Hope it helps...I'm not really sure exactly what your situation is, so if that's not clear, just post back and I'll help you some more.

Michael J

---

### Post by Forlong on 2007-11-26
> **TV-VCR said:**
> All I wanted to do was install some fonts for system wide use.
For .ttf fonts:
```
sudo nautilus /usr/share/fonts/truetype
```
Drag & drop the font(s) in there.

---

### Post by qqzhenyi on 2007-11-26
I assume you put the ttf file in your desktop

1) sudo mv /home/username/Desktop/aaa.ttf /usr/share/fonts/truetype/
(when asked for password enter YOURS)
2) sudo chmod a+r /usr/share/fonts/truetype/aaa.ttf
3) sudo fc-cache -f -v
4) restart X

---

