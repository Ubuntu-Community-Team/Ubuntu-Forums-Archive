---
title: "Killed my GUI, help!"
date: 2006-05-11
forum: Desktop Environments
---

### Post by 0MG on 2006-05-11
So, I got curious and decided to try to upgrade to dapper. I went in to my sources.list and changed all of the breezy references to dapper. When I rebooted, it puked. It tried to start x, but the screen flickered a few times and then asked if I wanted to view the log, eventually dumping me to a cli login prompt.

My basic question is, what are the repositories I need to have to make sure I am getting all of the correct files? I'm hoping an apt-get upgrade with the correct info will fix me. I will format if necessary, but that's a last resort.

---

### Post by Ptero-4 on 2006-05-11
You should change to vesa or basic ati/nvidia drivers. It's a compatibility problem with the drivers. Also ensure that the xorg.conf haven't been messed up bad.

---

### Post by 0MG on 2006-05-11
[QUOTE=Ptero-4]You should change to vesa or basic ati/nvidia drivers. It's a compatibility problem with the drivers. Also ensure that the xorg.conf haven't been messed up bad.[/QUOTE]


I'm sorry if this is very basic, but how do I go about changing the drivers? Also, what kind of things should I watch out for in my xorg.conf?

I know networking, but this stuff is a bit beyond me.

Appreciate your help!

---

### Post by art on 2006-05-11
You need to edit the file /etc/X11/xorg.conf
```
sudo gedit /etc/X11/xorg.conf
```
and here look for a section similar to 
```
Section "Device"
        Identifier  "ATI Technologies, Inc. FireGL V3100 (RV370)"
        Driver      "ati"
        BusID       "PCI:5:0:0"
EndSection
```

and change whatever stands instead of ati to vesa. Reboot and see if it works

---

### Post by 0MG on 2006-05-11
Thank you for your reply.

I went in and changed sis (my video driver) to vesa, saved the file, and rebooted but no luck.

It looks like that whole file might be trashed. After looking through the log, it says that there is no such module for the keyboard and touchpad and whatnot. Any advice on how to proceed?

---

### Post by Sef on 2006-05-15
Try this:

At the session login change to Terminal.  Once there type these commands:

sudo apt-get update

sudo apt-get install ubuntu-base unbuntu desktop

sudo apt-get dist-upgrade

---

