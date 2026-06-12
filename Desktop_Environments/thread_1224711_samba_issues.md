---
title: "samba issues"
date: 2009-07-27
forum: Desktop Environments
---

### Post by num on 2009-07-27
Hello,

I got Ubuntu 8.04 LTS with LUKS installed. I got Samba installed as well but I cannot access any directory from my Windows computer. When I try I get an error saying "directory not available or you have no permission" on the Linux computer I checked everything. What to do?

---

### Post by jasonbrisbane on 2009-07-27
Hi,

Set guest access on samba.
Allow plain text passwords.


That got it working for me.

---

### Post by num on 2009-07-27
well i did check every box on there or is this something i need to do in the config file?

---

### Post by swerdna on 2009-07-28
Well it might be the firewall or name resolution or [permissions. Try turning the firewall off temporarily as a diagnostic test. What is your Ubuntu firewall (ufw?).

Next check that the workgroup name on the Samba server is the same as the workgroup name on the xp box.

If that doesn't help run these commands in a terminal window to get a fairly full diagnosis and copy the returns you get back here:
[LIST=1]
[*]sudo ufw status
[*]sudo /etc/init.d/samba status
[*]smbtree -N
[*]ls -l /var/lib/samba/usershares
[*]testparm -s
[*]cat /etc/samba/smb.conf | grep workgroup
[/LIST]

---

### Post by jasonbrisbane on 2009-07-28
Hi,

Sorry, yes I meant on the Samba Config file, not on the Windows boxes.

Windows by default sends all passwords in plain text (go figure?).
So you need to tell Samba that.

There is a Samba program that you can use (gsambad?) that will allow you to set the samba config file.

I set the options there, clicked save and restart samba and that did it for me.

---

