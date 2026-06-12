---
title: "Accessing shares"
date: 2005-06-05
forum: Desktop Environments
---

### Post by Linuxnewby on 2005-06-05
I have installed Samba, and I have shared a folder containing windows files. I am using standard windows share settings.

I am trying to access this share from a windows xp machine. I can map to the share, and when I do the password prompt comes up, but nothing I type in is being accepted.

Any ideas?

---

### Post by KLineD on 2005-06-05
[QUOTE=Linuxnewby]I have installed Samba, and I have shared a folder containing windows files. I am using standard windows share settings.

I am trying to access this share from a windows xp machine. I can map to the share, and when I do the password prompt comes up, but nothing I type in is being accepted.

Any ideas?[/QUOTE]

So you say you can see the Linux machine on Windows (the shares) and even prompts for a password. If security is set as "user" in smb.conf then the user/pass it is asking for is your user/pass for your current linux account. If it's not set as user then my advice is to set it up as user, it's the recommended behaviour anyway.

---

### Post by Linuxnewby on 2005-06-05
"If security is set as "user" in smb.conf "

How do I check this?

---

### Post by not_yet on 2005-06-05
/etc/samba/smb.conf

---

### Post by KLineD on 2005-06-05
you really should take a look at the ubuntu guide: [http://ubuntuguide.org](http://ubuntuguide.org)

You can read there how to properly configure samba, add network users and all related things. 

All the configuration for samba is done editing the smb.conf file, located in /etc/samba/smb.conf as not_yet said.

---

