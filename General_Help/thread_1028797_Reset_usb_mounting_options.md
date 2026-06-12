---
title: "Reset usb mounting options"
date: 2009-01-02
forum: General Help
---

### Post by kesre on 2009-01-02
Hi,
I'm fairly new to ubuntu; trying to get linux to recognize a usb flashdrive as different from a mounted partition of the hard disk (for icons), I changed the mount point from /media/disk-1 to /media/usb-1

so how do I manually mount it in terminal with correct settings?

---

### Post by mc4man on 2009-01-02
> I changed the mount point from /media/disk-1 to /media/usb-1
How did you  change the mount point?

Does the drive no longer mount? (newline error

---

### Post by kesre on 2009-01-02
I used the GUI - right clicked the already mounted drive, Properties>Volume>Settings then typed  "/media/usb-1" in mount point

yeah, it doesn't mount -
"mount_point cannot contain the following characters: newline,G_DIR_Separator (usually /)"

-which is weird, since it worked when the default mount point was /media/disk-1

Anyhow, hope that helps. Let me know if you need any more details

---

### Post by mc4man on 2009-01-02
To fix run this in a terminal (leave flash drive out

```
gconf-editor
```

Scroll down to System -> storage -> volumes. Expand the volumes tree and you see at least one entry. If there's more than one highlight each and look in the right side box. You'll see mount_point /media/usb-1  (or whatever you entered.

Right click on that entry -> edit key and in the pop up delete the value totally. (or see below

Now the drive should mount again to the default of /media/<volume label>

If drives(volumes) don't have a label they will mount to /media/disk (or disk-1, ect.) and will be displayed as <size> media.

While you can give it a new mount point it's better to give it a volume label.  That way it will mount to /media/<volume label you picked> and will be displayed as  <volume label you picked>

If you want to do that, fix as shown, (deleting the complete value),  insert the drive and run this and post. (and pick a name you want to use, I'll show you what to do. 

```
sudo fdisk -l
```


If you just want to change the mount point in /media then you only enter the folder name, ie. usb-1 (so when your editing just leave usb-1

Also before re inserting the drive again make sure that the folder usb-1 doesn't exist in /media. When the drive is connected the folder will be created, when the drive is removed the folder will be deleted

See 2 screens, first shows new mount point improperly done. second one shows correct manner

I'd suggest that giving the drive a name (volume label) is the best option

---

### Post by kesre on 2009-01-02
Awesome

Thanks so much!

... Now, do you know how to get 
/usr/share/icons/(Theme)/(size)/devices/drive-removable-media

to be used for that usb drive icon instead of 
/usr/share/icons/(Theme)/(size)/devices/drive-harddisk
?

(the files might have a different name as well, like gnome-dev-harddisk
and gnome-dev-harddisk-usb, I just want the usb to be recognized as different from a partition of the hard drive)

---

### Post by mc4man on 2009-01-03
Well I never tried (will do so in a bit ) but right click on the the drive icon -> properties and click on the icon in the top left corner.

Then you'd browse to and open the appropriate icons folder, when that loads pick the icon of your choice.

Edit : you can give it any icon you want, note that on the desktop and in places -> computer are treated separately. (and can have the same or different icons

---

### Post by kesre on 2009-01-03
Ok, that takes care of the icon in Desktop, media, and Computer folders.
Is there a way to change it in the Places drop-down menu and Filebrowser sidepane?

(thanks again for all the help)

---

