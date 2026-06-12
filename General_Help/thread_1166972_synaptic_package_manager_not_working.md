---
title: "synaptic package manager not working"
date: 2009-05-22
forum: General Help
---

### Post by ecekarthic on 2009-05-22
Hi All,

I'm using Ubuntu 9.04. When i was installing something, my laptop went down and after that whenever i try to install something using synaptic package manager, I get the error 

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

But when I run sudo dpkg --configure -a in terminal window, I get the following error. 

root@karthic-laptop:/home/karthic# sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0037' near line 1:
 newline in field name `#padding'

What should I do? Is there any way to solve this. I can not install anything.

Regards,
Karthic

---

### Post by colau on 2009-05-22
> **ecekarthic said:**
> Hi All,

I'm using Ubuntu 9.04. When i was installing something, my laptop went down and after that whenever i try to install something using synaptic package manager, I get the error 

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

But when I run sudo dpkg --configure -a in terminal window, I get the following error. 

root@karthic-laptop:/home/karthic# sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0037' near line 1:
 newline in field name `#padding'

What should I do? Is there any way to solve this. I can not install anything.

Regards,
Karthic

Try with this
```

aptitude clean 
aptitude update
dpkg --configure -a
aptitude update

```
Which software were you installing?

---

### Post by plucky on 2009-05-22
I think you may have to delete the file.If the commands in the previous post don't solve your problem,then try these commands ```
cd /var/lib/dpkg/updates/
ls
sudo rm 0037
```

The ls command will list all the files in that directory.Delete the offending one which is 0037.

Good Luck

---

### Post by ecekarthic on 2009-05-22
Hi,

Thank you for your reply. It got resolved by removing the entire contents of /var/lib/dpkg/updates and renaming available-old to available

The entire set of commands is given below

root@karthic-laptop:/var/lib/dpkg# rm -rf updates/*
root@karthic-laptop:/var/lib/dpkg# cp available available.bak
root@karthic-laptop:/var/lib/dpkg# cp available-old available
root@karthic-laptop:/var/lib/dpkg# sudo dpkg --configure -a

Thank you guys,

Karthic

---

