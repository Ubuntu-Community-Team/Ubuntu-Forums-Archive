---
title: "shares on my xp-machine"
date: 2006-01-26
forum: Desktop Environments
---

### Post by groova on 2006-01-26
hi there. newbie speaking.

searched the forum, but found not the answer to my problem. :( on the propable chance that i missed something, here's my issue: 

got ubuntu set up on my laptop, connected to my xp machine via crossover. that one got a norton firewall, but it trusts my laptop.

internet connection from laptop via xp works.

got samba-server installed and up and running. 

i can now actually see my shared home-dir from the xp-machine. :KS 

but not such joy from my ubuntu-machine. when trying to connect to my windows shars, i only get login notices. i fill them in properly (same user/pwd on both machines AND samba), but they keep coming back. and when i cancel them, i just get ACCESS DENIED.

i tried smbclient -L xp-name, but no joy either.

also, i can install the shared windows printer and print a testpage. it sais "printing", but nothing comes out.

what am i doing wrong?


edit:

ps: pinging the xp-machine works.

---

### Post by jferrando on 2006-01-26
I usually access smb (windows/samba) shares mounting them.
From konquedor, you can also try to open the share using:

*smb://servername/sharename*

I don't remember the exact mount syntax, I have it enabled in fstab:

*//192.168.8.5/datos  /home/jferrando/surera  smbfs  credentials=/etc/smbc.jordi,uid=1000,gid=1000,noauto  0  0*

The file **/etc/smbc.jordi** contains:
[I]username = myusername
password = mypassword[/I]

Then I mount the share with
*$sudo mount /home/jferrando/surera*

---

### Post by jferrando on 2006-01-26
This is the syntax,

*$ sudo mount -t smbfs //192.168.8.5/datos /home/jferrando/surera -o username=[COLOR="Red"]your_username[/COLOR],password=[COLOR="Red"]your_password[/COLOR],uid=[COLOR="Blue"]1000[/COLOR],gid=[COLOR="Blue"]1000[/COLOR],codepage=unicode,iocharset=utf8,unicode*

uid and gid must be replaced by your correct linux uid and number, in case they are not uid=1000, gid=1000.

---

### Post by groova on 2006-01-27
:oops:

and how do i find my uid and gid? me new to this...

---

### Post by GnuSense on 2006-01-28
```
cat /etc/passwd | grep *username*
```

Obviously insert your username in the line above.  You'll see a line like this:

> *username*:x:500:500:*Real Name*:/home/ed:/bin/bash

The first number should be the UID, the second the GID.

---

