---
title: "samba"
date: 2005-12-15
forum: General Help
---

### Post by davebradford on 2005-12-15
i am having a lot of problems making samba work between my ubuntu server machine and my windows xp machine? is there any chance someone could post my up an 'ideal' config for samba just get things setup right..?

thanks

---

### Post by lutrafobic on 2005-12-15
If you just want the XP machine(s) to be able to access a specific folder this might be helpfull:

```
sudo nano /etc/samba/smb.conf
```

```

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = YOUWORKGROUP
   security = SHARE

[upload]
Path=/the_path_to_the_folder_you_want_to_share
read only = yes
guest ok = yes


```

This will give ANYONE access, tho READ ONLY. Change the read only to NO, if you trust your network/firewall.

P.S. don't forget to restart afterwards
```
sudo /etc/init.d/samba restart
```

(hope I got it right, wrote from memory)



Edit:    Setting up the 'hosts' files on both XP and Linux machine(s) will perhaps help too.
Linux = /etc/hosts
Windows = c:\windows\system32\drivers\etc\hosts

---

### Post by az on 2005-12-15
[QUOTE=davebradford]i am having a lot of problems making samba work between my ubuntu server machine and my windows xp machine? is there any chance someone could post my up an 'ideal' config for samba just get things setup right..?

thanks[/QUOTE]
First things first, Ubuntu only installs the samba client by default.  You need to install the samba server for other machines to see you.  The samba package installs everything you need.

This may not even be your problem,though, just covering the bases.

---

### Post by davebradford on 2005-12-15
thank you so much that works brilliantly must have been a problem with my conf.. how can you setup users from this but more importantly how can i delete all the users that i have already added!!

---

### Post by Kintar on 2005-12-15
[QUOTE=davebradford]thank you so much that works brilliantly must have been a problem with my conf.. how can you setup users from this but more importantly how can i delete all the users that i have already added!![/QUOTE]

If you've used the default settings, you should be able to add users by adding them with the standard useradd command, then use:

```

smbpasswd -a <username>
```

to add them to the samba user registry and set their samba password.  I believe there's a default setting that synchs samba and unix passwords, but it's been so long since I screwed around with it that I don't recall off the top of my head.

Oh, and removing a samba user is just another flag on smbpasswd.

-- Kintar

---

