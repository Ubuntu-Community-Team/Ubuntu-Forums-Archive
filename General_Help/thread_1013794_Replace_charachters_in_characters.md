---
title: "Replace charachters in characters"
date: 2008-12-17
forum: General Help
---

### Post by jim.lindqvist on 2008-12-17
Hello everyone, 

I am in a bit of a corner here.

Our company have a sftp server to allow customers to upload information to us. One of the customers have uploaded a complete structure but we can't download it. 

The problem seems to be because there are Swedish characters in the file names. 

Is it possible to replace every å, ä and ö on every file and folder under /home/customer026 in just a few short command.

Best Regards

Jim

---

### Post by albandy on 2008-12-17
tar the folder contents and download the tar file

tar cvf /tmp/contents.tar /home/customer026

---

