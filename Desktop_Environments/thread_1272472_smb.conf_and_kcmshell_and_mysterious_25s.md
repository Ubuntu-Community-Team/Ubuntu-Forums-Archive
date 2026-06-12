---
title: "smb.conf and kcmshell and mysterious 25s"
date: 2009-09-22
forum: Desktop Environments
---

### Post by frubblezuck on 2009-09-22
This is a question about Samba and kcmshell. I apologize if it's been answered elsewhere; I did look.

I recently used kcmshell's samba module to configure filesharing after it was already up and running. I generally didn't pay attention to whether it continued to run or not later on because I generally access shares on other machines opposed to accessing my Kubuntu machine's shares. It had stopped running. After running /etc/init.d/samba start enough times to make my eyes and fingers bleed, I look in the log.smbd file and it states it cannot reopen the "file:///var/log/samba/log.smbd", among other files it cannot find or open...thus samba services fail to start(though the /etc/init.d/samba start  command produces an [OK} when run).

So I open /etc/samba/smb.conf and I find some weird garbage like "file:///var/log/samba/log.%25m" and find these "25"s throughout the file in odd places stuck between several of the macros like "%25U". Is this coming from kcmshell trying to rewrite the smb.conf file or is this garbage introduced by an update? 

I removed the "file:///" prefixes and replaced them with "/" and removed all these odd "25"s that just magically appeared in the smb.conf file and ran the start command again and it's running fine.

Another thing I noticed about the kcmshell samba module was that it would _not_ allow me to add users...I imagine because the passwd command was written/rewritten as "file:///usr/bin/passwd %25u". 

Packing errors, bugs, or what? Thanks.

---

### Post by krazyd on 2009-09-22
"%25" is the URL escape sequence for the "%" character.

Not sure why they would cause a problem in a URL such as file://

---

