---
title: "Xfce notifications ruined"
date: 2010-06-15
forum: Desktop Environments
---

### Post by kempy1000 on 2010-06-15
Hi,

Xubuntu.

In an attempt to enable me to send custom notifications to my xfce desktop I installed libnotify-bin, notification-deamon, and notify-osd.

Now I can send notifications but they are ugly! Like the ubuntu ones I saw back in Hardy. Does anyone know how I can restore the notifications to the new black "bubble" look?

Network manager also uses this theme now to notify me of conenctions?

Thanks
Chris

---

### Post by kempy1000 on 2010-06-15
I am looking for this type of notify:
[https://wiki.ubuntu.com/NotifyOSD?action=AttachFile&do=get&target=notification-bubble.jpg](https://wiki.ubuntu.com/NotifyOSD?action=AttachFile&do=get&target=notification-bubble.jpg)

---

### Post by kerry_s on 2010-06-15
all you need is 1, you currently have 3 installed.

you need "libnotify-bin" that gives you notify-send.

you only need 1:
xfce4-notifyd
or
notification-deamon
or
notify-osd

more then 1 & your system is fighting with it self.
notify-osd is the standard ubuntu.

i prefer zenity for custom notifications.
run example:
zenity --info --text="this is a test"

---

### Post by kempy1000 on 2010-06-15
Thank you so much!! :)

I was really starting to miss them then!

I had libsexy or something still installed so when I did:
```

sudo aptitude purge xfce4-notifyd notification-deamon

```
it removed that which seamed to make it work!

The reason I dont use zenity is because this is a media machine connected to a tv and I very rarely get the mouse or keyboard out. So its just for little things like new emaile etc. Zenity would get in the way of the telly from what I can gather!

Chris

---

### Post by kempy1000 on 2010-06-15
Sorry to keep pestering its sorted :)

A quick reboot :)
Thank you again

---

