---
title: "Those mounted Drive icons on the Desktop...."
date: 2005-10-14
forum: Desktop Environments
---

### Post by Tails on 2005-10-14
Hi! my Drive has a quite a bit of partitions, so, ubuntu automatically mount them for me, but after they are mounted, they place them on the Desktop, so, my Desktop now has 6 mounted drives icens, (which i dun like to have iceons on my desktop), is there any ways to delete those from desktop or stop ubuntu to place those to Desktop (But I stilll want to keep auto-mount function)??

Thanks a lot for any helps!... :D

---

### Post by soul_rebel on 2005-10-14
gnome-panel:
applications->system tools->configuration editor

in configuration editorl:
apps->nautilus->desktop
on the right:
uncheck "volume_visible"

---

### Post by manicka on 2005-10-14
If they are fat32 partitions I use this type of fstab entry to mount them but not have them appear on the desktop.

```
/dev/hda7       /mnt/win_d       vfat     defaults,rw,umask=000 0 0
```

I use this because I like to still have cd/dvd's etc mount on my desktop when using them.

---

### Post by codejunkie on 2005-10-14
[quote=Tails]Hi! my Drive has a quite a bit of partitions, so, ubuntu automatically mount them for me, but after they are mounted, they place them on the Desktop, so, my Desktop now has 6 mounted drives icens, (which i dun like to have iceons on my desktop), is there any ways to delete those from desktop or stop ubuntu to place those to Desktop (But I stilll want to keep auto-mount function)??

Thanks a lot for any helps!... :D[/quote] press atl+F2 then enter ```
gconf-editor
``` then navigate to apps/nautilus/desktop and uncheck the box that says volumes_visible
hope this helps.

---

### Post by Tails on 2005-10-14
Thanks a lot guys, it works.. :D

---

### Post by hubbadub on 2005-10-19
thanks guys!

---

### Post by dvorack on 2006-01-09
seriously, thanks guys
i was asking myself the same question
:)

---

### Post by peterbras on 2006-02-23
And how can I hide the icons in Nautilus and "Places"?

---

### Post by mcduck on 2006-02-23
If you don't want them to show in places, you'd better edit your fstab to mount those partitions to /mnt instead of /media.

---

### Post by curley_sue on 2006-02-23
I have the opposite problem:
my mounted partitions (NTFS and FAT32) do not appear any longer on desktop, Places menu and in Nuatilus (only under /media)

tried /etc/init.d/dbus restart
 works BUT - then auto mount of CDs and USB wont go...
AND thant's no solution for reboot...

pls HELP!!!

---

### Post by shreg on 2006-12-27
Hello,

As for me I'd like to know how to change the name of those mounted drive on the desktop.
I've one drive who rename itselfs from something like : "acerdata" to a matrice like icon :
```
-|O O|
 |1  7|
```
And I'd like to change the name to somthing more understandable.

Thanks

---

