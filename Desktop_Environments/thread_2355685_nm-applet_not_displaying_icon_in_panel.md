---
title: "nm-applet not displaying icon in panel"
date: 2017-03-15
forum: Desktop Environments
---

### Post by jim-anderson on 2017-03-15
I've just installed Ubuntu 16.04 with Openbox and tint2 on my laptop. Most things are working, but not everything yet. Several icons which have appeared in the past are not showing up. For example, I have an entry for nm-applet in my openbox/autostart file. I have confirmed that the call to nm-applet is actually being made, but the icon does not show up in the systram area of the tint2 panel. I'm using a tint2rc file that only minor modifications to it and which has worked on other systems. It has an entry:


    > # Panel
     > panel_monitor = all
     > panel_position = bottom center horizontal
     > panel_items = LTSBC


The code 'S' specifies that the icons should show up in the notification area. The 'B' and 'C' codes are for the battery and clock, both of which are displayed.

If have been searching the net for hints and have found some, but none seem to work for me. One issue mentioned the file '/etc/xdg/autostart/nm-applet.desktop', which looks like this:

     > [Desktop Entry]
    > Name=Network
    > Comment=Manage your network connections
    > Icon=nm-device-wireless
    > Exec=nm-applet
    > Terminal=false
    > Type=Application
     > NoDisplay=true
    > NotShowIn=KDE;GNOME;
    > X-GNOME-Bugzilla-Bugzilla=GNOME
    > X-GNOME-Bugzilla-Product=NetworkManager
   > X-GNOME-Bugzilla-Component=nm-applet
   > X-GNOME-UsesNotifications=true
   > X-Ubuntu-Gettext-Domain=nm-applet

I deleted the 'NoDisplay=true' line and that had not effect.


I tried running nm-applet as a command line and that also had no effect. It gave a return code of 0 (success).

Can anyone help?

Jim Anderson

---

### Post by o9000 on 2017-03-15
It would be useful to see the tint2 output. Open a terminal, run killall tint2, then tint2 1>out.txt 2>err.txt. Let it run for a few seconds then kill it with ctrl+c, and post the two files.

You can also kill nm-applet and start it from a terminal, to record its output the same way (but change the file name).

---

### Post by jim-anderson on 2017-03-15
@o9000

I have attached out.txt and err.txt as you requested. I hope it helps.

BTW, I was looking closely at the tint2 panel and there is no space dedicated for my systray. This could mean there is no systray. Or it could mean no space was allocated since the nm-applet icon, and no other icons, were displayed.

Jim

---

### Post by o9000 on 2017-03-15
What we should see there is a message starting with add_icon and Network or NetworkManager in the name as in the attached screenshot.

Since there is none, nm-applet is not trying to create a systray icon. That could be due to various reasons, such as:

* it is not running
* it is stuck
* it is configured to hide the icon
* another systray is running in another panel

I'd rrestart nm-applet first. Kill it and start it again.

---

### Post by jim-anderson on 2017-03-15
Interesting. When I killed nm-applet and restarted, I got error message on the screen which I captured. Right now I don't know how to interpret the error messages, but I'm attaching a file with the messages. Hopefully, you can interpret them.

Jim

---

### Post by jim-anderson on 2017-03-16
This thread is being closed. It is being discussed on the Bunsenlabs forum under 'Help & Support'

---

### Post by QIII on 2017-03-16
It is?

---

