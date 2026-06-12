---
title: "mapped as \\ubuntu\sda public hard disk"
date: 2009-05-19
forum: General Help
---

### Post by kanolsen on 2009-05-19
I have a problem, I set up a ubuntu server and mapped it from windows with \\ubuntu\sda public hard disk

Then I reinstalled and changed name so I now map up with \\ubuntu\ntfs.

The problem is that one application Photoshop elements still look for the files in \\ubuntu\sda public hard disk, and even though the files are in the correct folder, the application failes as it shows the pictures as offline so I can't access them.

Question: Where do I insert the information so I mount it as \\ubuntu\sda public hard disk again? Is it an problem to temporarily change the name to sda.... and back to ntfs again, when I have fixed the Photoshop elements problem?

I have changed the /etc/samba/smb.conf file so it read: 
[sda public hard disk]
comment = public folder
path = media/store
public = yes
guest ok = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup

(is there other files I have to change?)

Thanks for all help
Kanolsen

---

