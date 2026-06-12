---
title: "sneeking in Ubuntu - student Windows 2003 server login"
date: 2008-03-28
forum: Education &amp; Science
---

### Post by gregstyles on 2008-03-28
Does anybody know of a program that will prompt students for a windows user name and password and then use this to mount their 'My Documents' from a Windows 2003 server?

Thanks

---

### Post by chungy on 2008-03-28
you can just go to Places -> Network

---

### Post by gregstyles on 2008-04-02
True, but not practical for young students. 

 I am looking for a program that:
 -  can be pre-set for the server and share name, 
 - will prompt the student for a username and password
 - will mount the share

---

### Post by urgnom on 2008-04-03
A simple way of doing this is to write a little script that utilizes smbmount. Put a gui/dialog box on top if you want, then apply 

smbmount //sambaserver/username /localmountpoint -o workgroup=workgroupname, user=username.

That's what I did for my own desktop, 'cause I need to mount samba directories all the time... hope it helps :)

---

