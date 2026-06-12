---
title: "Samba permissions - Strange problem"
date: 2006-08-06
forum: Desktop Environments
---

### Post by benjaminwr on 2006-08-06
Hi,

I am having a bit of trouble getting samba shares working on my network. Im using samba to share files betwenn my two ubuntu machines. I'm trying to share my documents folder with the laptop. Iv'e added my network user to smbusers and asigned it a password for samba. Both accounts are identical and  my local user to whom i've mapped my smbuser owns the files and directories in the folder but I still cant write to it

  security = user
  username map = /etc/samba/smbusers

  [Documents]
  path = /home/benji/Documents
  available = yes
  browseable = yes
  public = yes
  writable = yes

This is the relevant information and I'd rather not assign 777 to the folder since I have local users that I don't want to give permissions to.

I only want a specific user to be able to access the share that user being "benji" (the only one in smbusers and with smbpasswd)

Any help would be appreciated. Im sorry to post this but I have read loads of share for all users and public shares... etc. but I haven't found a user selective share.

Cheers

---

### Post by ertai on 2006-08-06
hi,

You could try the 777-permissions to look if the rights are the problem. If it still doesn't work you know the rights aren't the problem atm..

If it is the problem you should make sure that the samba-user (default nobody in nogroup) has the right to read (and write if you want to) the map

---

### Post by Haverhill Dave on 2006-08-06
I installed Ubuntu a few days ago on my PC and I wantto set up a network between my only linux machine and 5 windows XP machines. Yesterday my friend and I managed to access the XP pcs shared files and send a document for printing through the printer conected to the XP machine (it printed an ubuntu test page).
Apparently I dont have Samba server files on my computer, and I tries downloading them from [http://us3.samba.org/samba/ftp/Binary_Packages/Debian/samba/3/](http://us3.samba.org/samba/ftp/Binary_Packages/Debian/samba/3/)
Some of them worked, but others said "Error: Dependency is not satisfiable:..."
Please ca nsomeone help?

---

