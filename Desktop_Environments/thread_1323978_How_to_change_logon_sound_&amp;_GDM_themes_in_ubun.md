---
title: "How to change logon sound &amp; GDM themes in ubuntu 9.10"
date: 2009-11-12
forum: Desktop Environments
---

### Post by kyquangthai on 2009-11-12
I am using ubuntu 9.10
but i don't like default sound logon, i have some sound file .wav and i want change sound logon in ubuntu 9.10, but i don't know how to do,before i changed logon sound in ubuntu 9.04.
i have problem too with GDM themes.
Help me

---

### Post by zyxyellowxyz on 2009-11-12
> **kyquangthai said:**
> I am using ubuntu 9.10
but i don't like default sound logon, i have some sound file .wav and i want change sound logon in ubuntu 9.10, but i don't know how to do,before i changed logon sound in ubuntu 9.04.
i have problem too with GDM themes.
Help me

I, personally, have not figured out a way to change the GDM theme, but you can try the steps on this webpage: [http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html]("http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html")

As for the sounds, you can go to:
System > Preferences > Sound and change the sounds to what you want them to be. (See attached screenshots)

---

### Post by varsamakos on 2009-11-22
**kyquangthai**, you can change these sounds in /usr/share/sounds/ubuntu/stereo .

---

### Post by lamazavr on 2011-04-01
login sound you may change by editing "GNOME Login Sound" (*System->Preferences->Startup Applications*)
like this:

```
canberra-gtk-play  -f /usr/share/sounds/KDE-Sys-Log-In-Long.ogg
```

---

