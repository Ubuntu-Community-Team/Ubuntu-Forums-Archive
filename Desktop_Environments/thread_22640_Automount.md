---
title: "Automount?"
date: 2005-03-28
forum: Desktop Environments
---

### Post by Cklein on 2005-03-28
Hi, I've just installed kubuntu and i can mount cds dvds through konqueror...but once they get mounted i can't eject them, i've got to unmount... Is there some kind of automount in kubuntu?

---

### Post by telmo on 2005-03-28
Make sure you're mounting them as user. Like this...:

/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

---

### Post by Cklein on 2005-03-29
Thanks for your reply. My fstab is already like that. I can mount and unmount in an easy way through konqueror or typing in a console. But what I want is the cd/dvd getting mounted when I insert it and unmounted when ejecting it, so I'm looking for some kind of auto mount

---

### Post by Estariel on 2005-03-29
click on your panel,
select "add to panel",
select "applet"
select "storage media".

this will give you an applet that interfaces to HAL and will handle your mountin/unmounting needs very efficiently. I LOVE it... Best addition to KDE in a long time... :)


[edit]
this will not get your media automounted though. gnome-volume-manager does that for you. you can simply apt-get it, and just run it from the alt-F2 menu. at the end of your kde session, select "save session" and it will run gvm everytime you start kde.

---

### Post by getaceres on 2005-03-29
You can mount automatically a cdrom but you can't unmount automatically. That's a limitation of Linux itself, not KDE nor GNOME. If you want that you can use some kernel patches like submount and supermount but they are not safe since Linux was not designed to work this way.
It's better to mount and unmount it from the device manager (in the KDE panel).

---

### Post by Cklein on 2005-03-29
Thanks for your replies, it's nice to get answers so good and so fast, thanks again. So I installed the applet and the gnome-vol... stuff and it's great how it mounts automatically. But as 'getaceres' said I can't eject it, i've to unmount it. I thought that was changed in Linux. I 'come' from gentoo and I was used to ivman + hal (I guess) so I could use cd 'a la windows' withouth the need to mount neither to unmount it and it works great...but i like kubuntu, it's great...I don't want to go back, but there should be something else like that in ubuntu, it has to... Can someone help me with that? Can I help on some way to get it in kubuntu?

Thanks again
  Cklein

---

