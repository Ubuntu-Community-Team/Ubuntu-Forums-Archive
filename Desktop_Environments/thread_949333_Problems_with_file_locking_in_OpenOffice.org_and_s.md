---
title: "Problems with file locking in OpenOffice.org and samba over gnome-vfs."
date: 2008-10-16
forum: Desktop Environments
---

### Post by larseko on 2008-10-16
This post probably belongs in several forums, but Desktop is the most appropriate, as it mainly is a problem for desktop users in my the school environment which I'm in charge of.

We have several ubuntu Hardy clients that uses OpenOffice.org for editing files from samba shares on a Debian 4.0 box. Samba version is 3.0.24-6etch10. There are also some users using OpenOffice from XP, and some Mac users (both neooffice and OOo). The ubuntu clients mounts the samba share thru gnome-vfs (that is, places->connect to server->windows share).

The problem we have is that file locking between linux clients is not working. Users will write to the same files in the same shares simultaneously, causing data corruption and very angry users (yes, I find myself in a very tight spot now, and probably should get myself a copy of The Little Book of Calm). 

On the other hand you have the XP users. If a document is opened in Ubuntu, the XP user will open the file in read only mode. The other way around, when opened first in XP, the OOo on the ubuntu client will show a "general internet error" and close. Looks stupid, but is better than data loss.

I have tried turning secure locking off in samba, also to turn oplocks off, but there's no difference. Also, I can find no lck files on the samba server, if there should be any. 

Does anyone have any solutions to this, or some troubleshooting tips? This is, together with the fact that external displays (on laptops) barely works in Hardy, a very good reasons for the user base (teachers) to want to abandon the whole linux project. Really, there must be some way for samba to lock files, even if OpenOffice.org's file locking scheme is badly flawed?

Thanks in advance. Please tell if you need more info to be able to help.

---

### Post by dmizer on 2008-10-16
I would strongly suggest looking to the Open Office support forum for your answers to this problem. Here's a starter: [http://user.services.openoffice.org/en/forum/viewtopic.php?f=15&t=10096](http://user.services.openoffice.org/en/forum/viewtopic.php?f=15&t=10096)

---

### Post by larseko on 2008-10-16
Yeah, I've also joined the samba and OOo user mailinglists (not posted to OOo list yet), From that thread you linked to it looks as if OOo developers have pushed the responsibility for file locking down to OS level, which sounds unfortunate for cross platform environments.

---

### Post by larseko on 2008-10-17
It seems like there is no solution for this, other than upgrade to OOo 3.0, which isn't quite ready for Norwegian (nn) yet. I'll report how that works.

---

### Post by Michael REMY on 2009-06-23
in OO3, the problem stills the same : Xp users make the .lock directly to the server !

It is very unuserfriendly to ask them to open file in readonly mode...:confused:

---

### Post by dmizer on 2009-06-23
There is a fix for this posted in the second link in my sig.

---

