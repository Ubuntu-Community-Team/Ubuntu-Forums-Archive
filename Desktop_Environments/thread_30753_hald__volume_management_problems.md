---
title: "hald / volume management problems"
date: 2005-04-30
forum: Desktop Environments
---

### Post by aimaz on 2005-04-30
Hi,

I can't really tell what is going on, so I shall just list the symptoms I am experiencing.

1) Running gnome-volume-manager or gnome-volume-properties produces:

[FONT=Courier New]libhal.c 767 : org.freedesktop.DBus.Error.ServiceDoesNotExist raised
"Service "org.freedesktop.Hal" does not exist"[/FONT]

Followed by a message that claims hald is not running

[FONT=Courier New]$ ps -e | grep hald
6741 ?        00:00:00 hald[/FONT]

seems to show hald is actually running.

2) There are *alot* of hal related processes running.

[FONT=Courier New]init&#9472;&#9516;&#9472;10*[10-hal.dev]
.....&#9500;&#9472;42*[20-hal.hotplug]
.....&#9500;&#9472;hald[/FONT]

52 processes seems a little excessive  :-?

3) When I plug in my camera more 20-hal.hotplug processes are started but nothing happens apart from a short flurry of hard-disk activity.

[FONT=Courier New]$ pstree | grep hal
init&#9472;&#9516;&#9472;10*[10-hal.dev]
.....&#9500;&#9472;42*[20-hal.hotplug]
.....&#9500;&#9472;hald
.....&#9500;&#9472;udevd&#9472;&#9472;&#9472;udev&#9472;&#9472;&#9472;20-hal.hotplug
[/FONT]

4) Restarting udev never completes.

[FONT=Courier New]# /etc/init.d/udev restart
 * Recreating device nodes...[/FONT]

is as far as it manages to get. The same happens if it is stopped then started.

[FONT=Courier New]# /etc/init.d/udev start
 * Mounting a tmpfs over /dev...                                                                      [ ok ]
 * Creating initial device nodes...[/FONT]

If anyone knows how to fix this, or can point me in the right direction I'd be very grateful.

In case anyone else is having the same problems. Here is how I am currently working around the problem so I can access the pictures on my camera this should work for other usb mass storage type devices like some MP3 Players and pen drives.

First I become root

[FONT=Courier New]sudo -s[/FONT]

then I watch the system messages to find out the device's name

[FONT=Courier New]tail -f /var/log/messages[/FONT]

Then I plug my camera into the usb port and watch the screen for a line like
[FONT=Courier New]Apr 30 08:30:40 localhost kernel: Attached scsi removable disk **sda** at scsi9, channel 0, id 0, lun 0[/FONT]

Then I make somewhere to mount the camera and mount the device there.

[FONT=Courier New]mkdir /mnt/camera
mount /.dev/sda1 /mnt/camera[/FONT]

Then I can use the device pretty much as normal.

Aimaz

---

