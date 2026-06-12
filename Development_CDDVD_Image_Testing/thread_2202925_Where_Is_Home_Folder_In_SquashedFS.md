---
title: "Where Is Home Folder In SquashedFS?"
date: 2014-01-31
forum: Development CD/DVD Image Testing
---

### Post by XsheepX on 2014-01-31
Hello,
I grabbed an ISO of Linux Mint and extracted the squashed filesystem. Then I unsquashed it. My question is, where are all the files that end up becoming the user's home folder? /root/ and /home/ are empty.
Thank you. :)

---

### Post by XsheepX on 2014-01-31
It appears that the directory in question is /etc/skel.
Correct me if I am wrong? Any extra information would be appreciated.
Thank you.

---

### Post by Portaro on 2014-03-06
The /etc/skel is the path to any config of new users by a customs appear and files config.

If you want do a remastering you have remastersys, and relinux, with GUI method to remaster all you need is copy your /home/user definitions include the hidden folders and put it on /etc/skel. Make the ISO and voilá you have a configured distro.

---

