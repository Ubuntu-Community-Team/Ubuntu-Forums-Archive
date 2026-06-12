---
title: "How to remove the updates?"
date: 2006-06-08
forum: Desktop Environments
---

### Post by ty2000 on 2006-06-08
I followed this thread [http://www.ubuntuforums.org/showthread.php?t=145068](http://www.ubuntuforums.org/showthread.php?t=145068) to setup aiglx on my laptop, but failed with blank white screen.:confused:  So I just remove the compiz to get the destop work. Today, after I installed the updates comes from the source:
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper aiglx
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
I can not see some of the chinese charactors and english charactors on the desktop bar and also in some applications. ](*,) 
So what I want to do is completely remove all the packages updated from that source. 
How can I do it?
Thanks!

---

### Post by stryderjzw on 2006-06-10
Well, aiglx/compiz works on my laptop.

But some of my chinese characters are not showing up as well.  It's probably the latest update.  Can anyone help?

---

### Post by TOPPEL on 2006-06-10
yes what i do when i found some corrupted .debs from the repositories was delete all of them.  i did 'updatedb' and then 'locate *.deb' to find the directory they were stored and and rm them.  to remove and reinstall i 

apt-get remove <pkg> ; apt-get install <pkg>

that seems to do the trick.

---

### Post by stryderjzw on 2006-06-10
Also, just a quick question, where do I check what are the latest updates in a repository?

---

### Post by TOPPEL on 2006-06-10
/var/cache/apt/archives/

---

