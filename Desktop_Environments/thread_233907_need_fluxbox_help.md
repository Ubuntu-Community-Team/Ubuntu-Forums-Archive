---
title: "need fluxbox help"
date: 2006-08-10
forum: Desktop Environments
---

### Post by raffytaffy on 2006-08-10
i instaled fluxbox...so far i figured out how to add menu items and such..i run nautilus in it..my problem is..my 2 external hard drives arent getting mounted..so i cant listen to music..i have /dev/sda and /dev/sdb which i need to somehow mount...whso what kind of script to i need to add and where do i ned to add it?

---

### Post by Rule on 2006-08-10
to get your HDDs to mount at boot you would need to edit your "/etc/fstab" file and that is quite easy to do. I would post mine but I dont have any other partitions.

---

### Post by raffytaffy on 2006-08-10
i see...im worried however..would this mes up my gnome ..which is perfect..and i dont wanna start fiddling with things which can break it:(
sidenote - gnome mounts everything perfectly

---

### Post by taurus on 2006-08-10
Adding two entries in /etc/fstab to mount your two harddrives have nothing to do with Gnome, KDE, Xfce4, fluxbox, or anything other window manager...

---

### Post by raffytaffy on 2006-08-10
ok im goin to add this ..tell me if it looks ok

<file system>   <mnt point>     <type>     <options>    <dump>  <pass>
/dev/sda        /media/WD        FAT32          ???         0       0
/dev/sdb        /media/My        FAT32        ????          0       0

im not sure what to put for dump and pass...also ..is fat32 spelled with capital letters or how??

---

### Post by orb9220 on 2006-08-10
This is my fat entry

/dev/hdd1       /home/orb/Drives/hdd1/     vfat    defaults,utf8,umask=007,gid=46 0       0

---

### Post by orb9220 on 2006-08-10
So yours ?

/dev/sda /media/WD vfat defaults,utf8,umask=007,gid=46 0 0
/dev/sdb /media/My vfat defaults,utf8,umask=007,gid=46 0 0

---

### Post by raffytaffy on 2006-08-11
cool thanks

---

### Post by drycellbattery on 2006-08-15
so you settled with the /etc/fstab solution?

What about for usb sticks or usb hard drives that won't always be mounted at boot time? I remember when I installed Ubuntu with my usb hd connected and in Gnome I couldn't mount them as it told me I didn't have permission. Removing the fstab entries fixed this

Maybe a bash script would be better, yet I don't know what to do with that.

Maybe one script to mount them with the mount command and another script to unmount them with umount. If the scripts can be used like application launchers it would be easy. I'm just learning fluxbox now so I don't know what it can do. I'm more familiar with Xfce but want fluxbox for using jack and ardour.

---

### Post by Ramses de Norre on 2006-08-16
A more simple solution is adding gnome-volume-manager to your .fluxbox/startup script, this is mine (for reference):
```
#!/bin/sh
# fluxbox startup-script:
#
# Lines starting with a '#' are ignored.

# You can set your favourite wallpaper here if you don't want
# to do it from your style.
#
#fbsetbg -f ~/images/wallpapers/140154main_image_feature_481_ys_4.jpg
#
# This sets a black background

/usr/bin/bsetroot -solid black

# This shows the fluxbox-splash-screen
# fbsetbg -C /usr/share/fluxbox/splash.jpg

# Other examples. Check man xset for details.
#
# Turn off beeps:
# xset -b
#
# Increase the keyboard repeat-rate:
# xset r rate 195 35
#
# Your own fonts-dir:
# xset +fp /home/ramses/.font
#
# Your favourite mouse cursor:
# xsetroot -cursor_name right_ptr
#
# Change your keymap:
# xmodmap ~/.Xmodmap



# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#
# unclutter -idle 2 &
# wmnd &
# wmsmixer -w &
# idesk &

#Monitoring tool
gkrellm &
kmix &
#insert Gnome
GSDPID=`pidof gnome-settings-daemon`
if [  "x$GSDPID" == "x" ]; then
gnome-settings-daemon &
fi
#makes the gnome-theme-manager work
gnome-settings-manager &
#Automount volumes
**gnome-volume-manager &**
#keep this export line just before "exec fluxbox &" !
export LC_ALL=C
# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.
exec /usr/bin/fluxbox &
# or if you want to keep a log:
# exec /usr/bin/fluxbox -log ~/.fluxbox/log

#Following lines execute programs after fluxbox is started
fbpid=$!

sleep 3
{
   fbpager -w &
   tilda &
} &

wait $fbpid

```

---

