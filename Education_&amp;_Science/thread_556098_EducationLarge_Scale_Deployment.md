---
title: "Education/Large Scale Deployment"
date: 2007-09-20
forum: Education &amp; Science
---

### Post by cjdevlin on 2007-09-20
Hello,
Just wondering what software people were using to control modifications to the hard drive.  Cornerstone is a windows based version of what I am looking for.  Network booting seems like an ok option, but I would like the machines to be able to stand alone.  

Thanks

---

### Post by UbuWu on 2007-09-21
What exactly do you want to do? To restrict what files users can use/modify, just create a restricted user account. If you want to set a limit on their disk usage, install quota to set disk quotas for them.

---

### Post by hsweet on 2007-09-22
You might want to check out Edubuntu and LTSP.  No local hard drives to worry about users changing, no client configuration at all.

If you want stand alone's I think there is a kisok mode you can set up if you use KDE

---

### Post by cjdevlin on 2007-09-24
What I am really looking for is something to negate any writes to the hard disk.  I just want students to be able to use email, ooo, and have access to their directory (using samba).

---

### Post by lisati on 2007-09-24
Just a thought: if your students are "doing email", you'll probably need some provision for cookies being used with webmail - there'd be no point if someone signed in, and then lost their session because of disk modirifcations being undone.

---

