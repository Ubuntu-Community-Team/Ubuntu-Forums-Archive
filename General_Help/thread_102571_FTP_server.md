---
title: "FTP server"
date: 2005-12-12
forum: General Help
---

### Post by DarkOra on 2005-12-12
Hello all im looking for a easy to use ftp server since my windows is kinda down at the moment I cannot use cerberus to host my current files for TPS and soon I will probably be doing most of my work on linux and only use windows for gaming. Any help would be great.

---

### Post by frodon on 2005-12-12
It depends of your needs, you could have a look to my Guide which explain how to set a ftp server with user access using proftpd : [http://www.ubuntuforums.org/showthread.php?t=79588](http://www.ubuntuforums.org/showthread.php?t=79588)
But there isn't, as far as i know, a "good" GUI based ftp server because a GUI is not really needed.

---

### Post by DarkOra on 2005-12-12
the ftp server doesnt need to have a gui im fine with command line and all i wanna do is share the files within a certian folder to users at TPS but restrict access to this one and only folder. I will have a look at your guide, ive tried proftpd but it wont let me access /etc/proftpd.conf and im using root privs in terminal when i try.

---

### Post by frodon on 2005-12-12
Well, my guide seems to fit with your needs however i don't understand why you get problems editing the proftpd.conf file. Do you get error messages when you try to open the file ? Do you have problems with some other root apps ?
By the way, i guess you use KDE so the command should be : ```
sudo kwrite /etc/proftpd.conf
```

---

### Post by DarkOra on 2005-12-12
ok i saw why I got the permission denied error their was a small error in my way of opening the file. But thanks for your help if I come across any errors I will  post them on the forums.

---

