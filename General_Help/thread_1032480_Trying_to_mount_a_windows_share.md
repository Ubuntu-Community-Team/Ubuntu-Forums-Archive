---
title: "Trying to mount a windows share"
date: 2009-01-06
forum: General Help
---

### Post by happyhacker on 2009-01-06
In root I am trying these commands:
# mkdir -p /mnt/win (that worked)
# mount -t smbfs -o username=winntuser,password=mypassword //windowsserver/sharename /mnt/win
# cd /mnt/win
# ls -l

I get as far as the 2nd one with:

# mount -t smbfs -o username=acdoruser1,password=!acdor2008 //192.168.1.66/acdorUser /mnt/win

and get the response:

bash: !acdor2008: event not found

Can anyone help. Essentially I am trying access to windows from the ubuntu server  8.10 because I cannot get backuppc to work as it times out when I try to do a backup so I thought I would test this route first.

---

### Post by HermanAB on 2009-01-06
Firstly, smbfs is deprecated.  Use cifs instead.

Secondly, Samba and funny characters in usernames/passwords do not play well together.  Get rid of the "!".

'Hope that helps!

Herman

---

### Post by happyhacker on 2009-01-06
OK, I'll change the password. What are the commands for cifs, the same but with "cif" instead of "smb"?

---

