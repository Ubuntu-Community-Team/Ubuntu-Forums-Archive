---
title: "trash bin disappeared"
date: 2008-06-09
forum: Desktop Environments
---

### Post by wwuster on 2008-06-09
I'm running gnome on 8.04. I noticed today that the trash bin icon on the task bar is gone. I tried to add it to the panel but it doesn't add. How can I get it back?

William

---

### Post by wwuster on 2008-06-09
> **wwuster said:**
> I'm running gnome on 8.04. I noticed today that the trash bin icon on the task bar is gone. I tried to add it to the panel but it doesn't add. How can I get it back?

William

After more searching I found that this is a known bug. I rebooted and I had 5 trash icons. They were there but just invisible. I also followed a suggestion in the bug report and edited a file /usr/lib/bonobo/servers before I rebooted. Anyway, it works now.

---

### Post by BigSilly on 2008-06-09
Yep, this fixed it for me too. Got it from Launchpad, but it sounds like a fix is on it's way -

> Edit: /usr/lib/bonobo/servers/GNOME_Panel_TrashApplet.server

Add this inside the <oaf_server location="/usr/lib/bla/trashapplet"> element
(NOT the one with the location="OAFIID:bla")

    <oaf_attribute name="bonobo:environment" type="stringv">
        <item value="DBUS_SESSION_BUS_ADDRESS"/>
    </oaf_attribute>

This works for me. [Bug report and fix here.]("https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/211604")

---

### Post by RuleMaker on 2008-07-22
Today, suddenly my trash disappeared from the panel. I cant get it back however I try, I tried to:
add a new trash to the panel
reboot
reinstall gnome-applets
add a trash icon to the desktop (from gconfig-editor), it's shown on desktop now but not working, when I double click it it says:
> Couldn't display "trash:".
There is no application installed for this file type

Now I am confused, what else could I try to get it back?
And now I noticed that i cant even open the "Computer", although all other directories are working.
I use ubuntu 8.04, please help.

---

