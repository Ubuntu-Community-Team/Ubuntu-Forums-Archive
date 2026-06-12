---
title: "Samba help"
date: 2006-01-16
forum: General Help
---

### Post by barqster on 2006-01-16
How can I make it so I can bypass the authentication part of logging on from a windows computer (if the OS matters)....

---

### Post by joft on 2006-01-17
Hi,

I use "security = share" in my smb.conf to solve this. Or did you mean something else?

---

### Post by jaywatkins on 2006-01-17
Hello,

How would one restart the Samba service from the terminal?

init.d samba ?

That does not seem to work

Thanx

---

### Post by barqster on 2006-01-17
Is there any way I can save the password on windows, so that when I restart either machines I don't have to enter the user name and password?

---

### Post by joft on 2006-01-18
Hi,

@jaywatkins: You have to do a "/etc/init.d/samba restart".
Generally this is the way (in Debian) to start/stop services:
"/etc/init.d/<service> start|stop|restart|..."

@barqster: I guess you have to ask M$ for this feature (saving password in Windows) ;-) . But I think, there is/was a checkbox in the username/password dialogue, so ....
Didn't "security = share" work for you? Or do you in fact depend on "security = user" (I guess you do have this now?).

---

### Post by dhanjel on 2006-01-18
Another question but within the topic; is it possible to auto-mount a ntfs partion  on another computer easily in samba?

---

