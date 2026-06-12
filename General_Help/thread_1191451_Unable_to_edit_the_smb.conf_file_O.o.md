---
title: "Unable to edit the smb.conf file O.o"
date: 2009-06-19
forum: General Help
---

### Post by grims_razor on 2009-06-19
Hi, i'm relatively new to linux in general. i've used ubuntu at work a lot as a troubleshooting tool, so i decided to do some research, and i decided to run ubuntu 9.04 as a file server. i have samba, swat, and winbind, and i've tried several different methods to edit the smb.conf file, but i'm still unable to do it. says i dont have the permissions to do so...even after creating a root account? Has anyone encountered this problem? or maybe there's something i had missed in the forums or documentation?

---

### Post by anystupidname on 2009-06-19
sudo gedit /etc/samba/smb.conf
sudo /etc/init.d/samba restart

if that doesn't work?!? post the permissions on the file
ls -hasl /etc/ | grep smb

---

### Post by dmizer on 2009-06-19
You said that you have the root account enabled. Though that's not ever necessary, do you actually have a root prompt when attempting to edit the file? It will look like this:
```
root@xxyyzz:/#
```
If not, then this should work:
```
sudo nano /etc/samba/smb.conf
```

---

### Post by grims_razor on 2009-06-19
Thanks Dmizer, i'll be trying that as soon as i'm off work today..hopefully that should clear things up for me.. I got a long way to go with linux, but i'm having good times with it figuring out things...this file has been the worst headache any linux has ever given me.

---

### Post by grims_razor on 2009-06-19
Once again, Thank you Dmizer, Worked like a charm :)

now that my problems lie elsewhere, i'll do some more searching into my challenges. But thank you again for the speedy response, i'd offer you something in return...but i'm not sure i'd be much of use.

Alas, this problem has been solved ^.^

---

