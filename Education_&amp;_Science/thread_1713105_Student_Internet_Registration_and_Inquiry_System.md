---
title: "Student Internet Registration and Inquiry System"
date: 2011-03-23
forum: Education &amp; Science
---

### Post by niallcd on 2011-03-23
A buddy of mine is helping a school create and manage their network. Hes run into a bit a wall on the student management side however. They don't really have much in their budget for expensive commercial software and I urging them to go the open source route. 

This community has always been great for guidance so I figured this would be my first stop in seeking advice. 

Basically they are looking for a system to manage students on their network.Ideally they would like students to log into the schools network using their student IDs thus allowing them to use and save work to a secure space on our servers. The idea is that students wouldn't have access to another persons work. It would also be useful to see students machines/desktops and have control over them should the need ever arise. For that I was thinking iTALC should do the job. 

Ubuntu server will be used for the file system. 

If anyone has any ideas about what software they should consider it would be fantastic. If any other information is required just let me know. 

Thanks in advance.

---

### Post by doas777 on 2011-03-23
well, for login, LDAP is probably the best bet, and it can integrate with samba for filesharing.

you may want to look into one of the more business/Enterprise-oriented distros like Fedora/CentOS or SUSE. they will likely have better tools and options for enterprise integration that ubuntu out-of-box.

---

