---
title: "No volume and brightness OSD in Gnome-Shell."
date: 2014-03-09
forum: Desktop Environments
---

### Post by cdysthe on 2014-03-09
Hi,

I no longer have volume and brightness OSD in Gnome-Shell. It was working and then of a sudden it's gone. I used to have a square popping up with either the volume or brightness. Both volume and brightness control works and I can hear the volume changing (popping sound) and see it in the system tray top right. Brightness control also works. I tried to create a new user account and in the new account I have volume and brightness OSD so something has changed in my user account. Any idea how I can get the volume and brightness OSD back?

---

### Post by Who needs windows anyway? on 2014-04-08
I have the same problem with my install of Ubuntu Gnome, it was working one minute and the the next it wasn't. The volume and brightness adjustments work but no on screen display to show level set.

---

### Post by keldwud on 2014-10-17
The notification program responsible for the pop-up with the volume and the brightness is notify-osd. It is called by the dbus service under the name org.freedesktop.Notifications and executed with the command Exec=<path to notification program of your choice>. In my case, I had installed xfce and then there were two files in /usr/share/dbus-1/services/<naming scheme foreign to me>.service that called the org.freedesktop.Notifications. I checked the whole folder by grepping for Name= and counting the results of non-unique results and found that every namespace in that directory was unique except for my notifications namespace. This led me to the solution of renaming the file that executed the xfce notifyd to service.disabled which made the file unreadable to dbus and then after a restart my volume and brightness notifications came back.

So a general more abstract method of resolving this issue for multiple users might involve grepping for org.freedesktop.Notifications in the /usr/share/dbus-1/services folder and then renaming any of the offending entries to anything that doesn't end in .service leaving only the path to the actual executable you wish to load and if it's not available, you can create one using the template below as a guide for adding your desired notification service. One could also theoretically call bash and use conditionals in the dbus service file as it allows for that and you could also use environment variables against a boolean check to select which notification program you want based on your desktop environment but I haven't finished getting that to work yet, I was just glad to get my volume and brightness indicators back. Anyway, here's the code, this is specific to my 64 bit ubuntu, there will be some slight modifications based on your environment and make sure you have installed notify-osd if it isn't installed already. I tried looking for an update-alternatives type method to switch it but this is the best I could come up with so far. This method will allow you to keep whatever other programs you installed that disabled it in the first place. I found other methods that just brute forced the issue by completely purging the programs that took its place but if you wish to keep the programs then this method is for you.
[FONT=fixedsys]
<favorite editor> /usr/share/dbus-1/services/org.freedesktop.Notifications.service
[D-BUS Service]
Name=org.freedesktop.Notifications
Exec=/usr/lib/x86_64-linux-gnu/notify-osd

[FONT=arial black][FONT=arial]Hope that helps.[/FONT][/FONT]
[/FONT]

---

