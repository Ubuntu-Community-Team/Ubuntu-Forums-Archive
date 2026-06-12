---
title: "printing on a win2k machine"
date: 2005-05-11
forum: Desktop Environments
---

### Post by mindspin on 2005-05-11
Hi everybody, 

I try to get printing on a w2k printer via smb working, but the KDE cups konfiguration does not work. It's not ubuntu, more kde specific, because I haven't got it getting to work on knoppix too. 

I tried it with using guest, anonymous, the win2k user, but it never works, the file is kept in  spool and never makes its way to the printer. I think its something with user/directory permissions but got lost meanwhile.

It is no problem to connect to the other smb shares on the win2k machine, so I do not think its smb related, more a cups issue.....

any help would be appreciated although I'd like a "paper free office" as it is right now.

---

### Post by improverrr on 2005-05-11
I will be the first to say i am far from being an expert on this.  I would take a look at your /etx/samba/smb.conf and see what it is looking like.  the printer info is down towards the bottom.  ALso remember if something is " # " out, it is just a coment.

take a look at yours, it should have a name labeled in this format [printer name].  look at the options for it listed underneath it and bump and compare with the following.  Tweak and experiment as required.

[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

---

### Post by mindspin on 2005-05-11
Hi, got it going just by selecting the correct driver, on knoppix there was no correct fothermucking driver listed. ( i use a hp printer/fax and there was only hp lj 3200m listed but kubuntu offered me the correct one (hp lj 3200m ljet4)

great!

mindspin

---

