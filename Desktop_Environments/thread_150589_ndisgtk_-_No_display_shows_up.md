---
title: "ndisgtk - No display shows up"
date: 2006-03-26
forum: Desktop Environments
---

### Post by Geffers on 2006-03-26
I've installed ndisgtk, ndiswarpper utils was already installed.

I've tried to run ndisgtk and all I get is some disk activity but nothing appears on my desktop.

I've tried running from the 'System, Windows Wireless Drivers option, the run dialog auto inserts gksudo /usr/bin/ndisgtk but I twigged the kde command and altered to kdesu /usr/bin/ndisgtk

I've tried running as my user permissions and as root, all to no avail ](*,) 

Any pointers appreciated.

Geffers

---

### Post by dralaroc on 2006-03-26
Same here, when I click on the windows wireless driver icon a password box pops up.  I type my password and in then nothing.

---

### Post by Geffers on 2006-04-13
[QUOTE=dralaroc]Same here, when I click on the windows wireless driver icon a password box pops up.  I type my password and in then nothing.[/QUOTE]

I got this reply from the 'newbie' section of the forum, my ndisgtk now works, all I've got to do now is get the WiFi working somehow :???: 

xxxxxxxxxxxxxxxxxxxx

Originally Posted by Retrix

This is a bug in the packaging, which I apologize for. It has been fixed in the dapper version.



To run ndisgtk, you'll need to install the python-glade2 and python-gtk2 packages installed.

xxxxxxxxxxxxxxxxxxxxxx

Geffers

---

