---
title: "DVD won't play in Blackbox/XFCE"
date: 2005-11-07
forum: Desktop Environments
---

### Post by stuoolong on 2005-11-07
Hi, hope someone can help.

It's not really a Gnome issue, but I couldn't find a more suitable forum. Basically, I've got a new DVD player/CD writer. It functions perfectly on Gnome (I'm using Totem-xine) but I want to play DVDs using Blackbox because my computer's very slow and the picture is jumpy on Gnome. However, when I try to play the DVD, using totem-xine, in either Blackbox or XFCE, I get the error message:

failed to find mountpoint for device /dev/hdc in /etc/fstab

I don't really see how it can be a mount issue though, because audio cds work fine on all three X window systems; it seems to be to do with the differences between them.

Here is the relevant line from file fstab:

/dev/hdc  /media/cdrom0  udf,iso9660,noauto  0  0

Puzzled.

---

### Post by Ampersand on 2005-11-07
Just to make sure, does the directory /media/cdrom0 exist? If so, what happens if you run
```
sudo mount -t iso9660 /dev/hdc /media/cdrom0
```

Also, for the video problems make sure that DMA is enabled for the drive by running

```
sudo hdparm -d 1 /dev/hdc
```

---

### Post by stuoolong on 2005-11-07
Directory /media/cdrom0 exists for sure.

In Blackbox, if I do:

$ sudo mount -t iso9660 /dev/hdc /media/cdrom0
Password:
mount: No medium found

However, when I do the same in Gnome, I get this:

$ sudo mount -t iso9660 /dev/hdc /media/cdrom0
mount: block device /dev/hdc is write-protected, mounting read-only
mount: /dev/hdc already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/hdc is already mounted on /media/cdrom0

I've switched on DMA as you suggested. No change in the problem yet. Thanks for the help so far!

---

### Post by Ampersand on 2005-11-07
A possible workaround might be to run
```
gnome-volume-manager &
```
followed by 
```
disown
```

CDs and other removable media should automount after that.

---

### Post by stuoolong on 2005-11-07
Nice one, it seems to work on Blackbox now! Thank you.

I don't quite get what I just did though. This command tells the computer to automatically mount any removable drive that it supports. Why, before I ran it, would audio CDs play from the same drive? What does the Disown bit do? Why the difference between Gnome and Blackbox?

---

### Post by Ampersand on 2005-11-07
Gnome volume manager is the process in Gnome that automatically mounts removable media.

The disown command allows you to close the terminal without it killing gnome-volume-manager. The & at the end of a command means 'run in background', allowing you to continue using the terminal. To bring a process back to the forground, use the command 'fg'. Not really usful in this case, but I thought it might be of interest to someone. (:

If you go to the Settings menu in XFCE, then "XFCE4 Sessions and Startup Settings" and enable "Launch Gnome services on startup" (under the Advanced tab), this should run the volume manager every time you run xfce. Not sure about blackbox, but there's probably a similar option (or somewhere to add commands to run on startup).

Blackbox and xfce are designed to take up less resources than Gnome, so they have less services running.

---

