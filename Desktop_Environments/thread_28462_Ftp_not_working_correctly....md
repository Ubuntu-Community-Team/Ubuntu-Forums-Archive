---
title: "Ftp not working correctly..."
date: 2005-04-20
forum: Desktop Environments
---

### Post by ryan.overton on 2005-04-20
I can use ftp via the terminal window and all works well....

but if I try to use gFTP or Nautilus to connect, it connects, but it just keeps 'recieving filelist" and stay there, then enters passive mode.

I had a similar problem on FC, and it was a firewall setting, but I understand Ubuntu's firewall is different.  any suggestions?

Thanks.

---

### Post by ming0 on 2005-04-20
As far as I know, Ubuntu is firewalless unless you install one yourself (firestarter)? However, I've been having problems with gftp in general (no matter what protocol--ssh or ftp). I just haven't been able to get it to transfer anything.

---

### Post by shakin on 2005-04-20
[QUOTE=ryan.overton]I can use ftp via the terminal window and all works well....

but if I try to use gFTP or Nautilus to connect, it connects, but it just keeps 'recieving filelist" and stay there, then enters passive mode.

I had a similar problem on FC, and it was a firewall setting, but I understand Ubuntu's firewall is different.  any suggestions?

Thanks.[/QUOTE]

Sounds like passive mode is on while it should be off, so change it in the preferences. Command line ftp defaults to off.

---

### Post by ryan.overton on 2005-04-20
Well.... hah.. dont I feel like the n00b.....  

that was it!!!!!

Now... how do you turn off passive mode in the Nautalus?



[QUOTE=shakin]Sounds like passive mode is on while it should be off, so change it in the preferences. Command line ftp defaults to off.[/QUOTE]

---

### Post by Jason-X on 2005-12-02
[QUOTE=shakin]Sounds like passive mode is on while it should be off, so change it in the preferences. Command line ftp defaults to off.[/QUOTE]

Thanks for the help. I was having the same trouble with Gftp. Nice one!!:KS

---

