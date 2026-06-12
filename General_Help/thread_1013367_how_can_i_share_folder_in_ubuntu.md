---
title: "how can i share folder in ubuntu?"
date: 2008-12-16
forum: General Help
---

### Post by mr_sukor on 2008-12-16
i found this note when i want to share the folder. 

'net usershare' returned error 255: net usershare add: cannot share path /media/Ghost/Entertainment/Mp3/surah as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = False" 
	to the [global] section of the smb.conf to allow this.

how can i solve this? 

p/s: sorry if i repeat this thread.. thank you.

---

### Post by spiderbatdad on 2008-12-16
Are you the admin of this computer? Do you want to change ownership of the directory or edit smb.conf?

---

### Post by amdalex on 2008-12-16
I have the same problem, I'm trying to share an external NTFS drive but it says I can't because I am not the owner of the drive. Root is, how can I claim ownership of it? thanks

---

### Post by jerome1232 on 2008-12-16
Based on that error message the way to do this would be do edit your smb.conf as it says.

Go ahead and pop open a terminal:

```
gksu gedit /etc/samba/smb.conf
```

Find the section that says [global] it's towards the top

Underneath add that line the error recomends

```
usershare owner only = False
```

save and restart samba

```
sudo /etc/init.d/samba restart
```

now try it, you *may* have to log out then log back in for the changes to take affect.

---

### Post by amdalex on 2008-12-16
I can't find the error section in the file?
Here is the global section
```
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast
```

---

### Post by jerome1232 on 2008-12-16
Just add "usershare owner only = False" under [global] and without the quotes, I was referring to the error message in post #1.

---

