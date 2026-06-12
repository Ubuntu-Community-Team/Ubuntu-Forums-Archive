---
title: "groups"
date: 2009-05-17
forum: General Help
---

### Post by texas.chef94 on 2009-05-17
The results of terminal command groups leaves me with questions.
1. I assume allen adm identifies me as the primary user.
2. What else besides dial out? wireless??
3. plugdev I understand
4. lpadmin has to do with printer I guess
5. Samba share I understand somewhat except is it by default, did I acquire it as an an upgrade or was it a result of an actual installation.

Its just an attempt to learn more and I appreciate any info

Allen

allen@allen-desktop:~$ groups
allen adm dialout cdrom plugdev lpadmin admin sambashare

---

### Post by geirha on 2009-05-17
There's probably a document somewhere explaining what the groups are used for, but I can't find any.

In general, the groups decide what device nodes you can access in /dev. The following command will list all device nodes owned by a certain group
```
find /dev -group cdrom -ls
```
As you may see from the above command, all cd devices have read and write permissions for members of the cdrom group. That means that if you are a member of the cdrom group, you'll be able to read and burn CDs and DVDs.

adm seems to be mainly used by log files in /var/log/, giving you read access to most of the logs if you are a member.

dialout gives you access to device nodes in /dev that allows you to connect to another computer via a modem.

plugdev is similar to cdrom, it gives you read and write access to pluggable devices like usb pendrives and sd cards.

lpadmin, as you guessed, allows you to add/remove printers

admin is mainly used by sudo. In the default /etc/sudoers, everyone that is a member of the admin group is allowed to use sudo to run applications as the root user.

sambashare, I don't know about that one. I haven't used samba for a long time, but it probably gives you access to some configuration files in /etc
```
find /etc -group sambashare -ls 2>/dev/null
```

Lastly, the first group listed, is your primary group. In Ubuntu, when creating a new user, a group by the same name is also created, and is made the primary group of that user. The reason you need a primary group is because when you create a file, it must have a user owner and a group owner, and so you must have at least one group membership for that.

---

