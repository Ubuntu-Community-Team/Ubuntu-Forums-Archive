---
title: "Can't change my Samba config file"
date: 2006-06-22
forum: Desktop Environments
---

### Post by mrpinknn on 2006-06-22
Hello,

New to everything.  So this might sound strange.  When I goto edit my Samba config file I can't.  I don't have permission to edit this.  I have read that you can't log on as root.  All I want to do is open the file and edit the file. How do I do this?

Thanks!!

---

### Post by drpaul on 2006-06-22
Just do

sudo gedit filename

You'll have to respond with your password. Then, Presto!

Paul

---

### Post by mrpinknn on 2006-06-22
Thanks.  But where do I do that?  What are the steps?  Thanks!

---

### Post by Thund3rstruck on 2006-06-22
applications > accessories > terminal

type * sudo gedit /etc/samba/smb.conf*

---

### Post by lamego on 2006-06-22
By your question you really should read some [guide]("http://ubuntuguide.org/wiki/Dapper") .

---

### Post by mrpinknn on 2006-06-22
Thanks that linked helped.  Now I have it working they way I want it to.

-pink

---

