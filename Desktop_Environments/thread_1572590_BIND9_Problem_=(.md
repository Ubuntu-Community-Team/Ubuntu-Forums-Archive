---
title: "BIND9 Problem =("
date: 2010-09-11
forum: Desktop Environments
---

### Post by cooldood on 2010-09-11
Hi. I recently installed Ubuntu 10.04 LTS Desktop on my SuperMicro Servertower. I have one problem though, that is that I cannot seem to get BIND9 to remove completely as I messed up one of the configurations. When I tried to install it again, it said that /ect/init.d/bind9 doesn't exist. And yes, I removed that file manually as it would not re-install it when I tried to use apt-get install bind9. So, if anyone could maybe distribute the default file, I would appreciate that, too. Any help would be great. 
Thanks.
Nick

---

### Post by hictio on 2010-09-11
> **cooldood said:**
> Hi. I recently installed Ubuntu 10.04 LTS Desktop on my SuperMicro Servertower. I have one problem though, that is that I cannot seem to get BIND9 to remove completely as I messed up one of the configurations. When I tried to install it again, it said that /ect/init.d/bind9 doesn't exist. And yes, I removed that file manually as it would not re-install it when I tried to use apt-get install bind9. So, if anyone could maybe distribute the default file, I would appreciate that, too. Any help would be great. 
Thanks.
Nick

Are you sure it is a LTS Desktop you are talking about? I have one of those ;) and there is no "/ect/init.d/bind9" file.

---

### Post by cooldood on 2010-09-11
> **hictio said:**
> Are you sure it is a LTS Desktop you are talking about? I have one of those ;) and there is no "/ect/init.d/bind9" file.

Well, I installed it via command line, and yes it originally had /etc/init.d/bind9. I just don't know what to do because I messed it up and now I can't re-install it because I removed it manually. Any suggestions? That was probably the stupidest thing I've done yet today. :o

---

### Post by hictio on 2010-09-11
I'm sorry, but I don't completely understand you.
You have a plain vanilla Ubuntu Lucid Desktop, with say, Gnome.
You installed bind9, using apt from the command line.
That ended Ok, that is, it installed fine.
When you were configuring it, something went south, and you decided to re-install it? How did you tried that? Have you been able to re-install it?
Then, you deleted by hand the file "/etc/init.d/bind9", and now you can't re-install bind9?
Is this pretty much what happened? :)

---

### Post by cooldood on 2010-09-11
> **hictio said:**
> I'm sorry, but I don't completely understand you.
You have a plain vanilla Ubuntu Lucid Desktop, with say, Gnome.
You installed bind9, using apt from the command line.
That ended Ok, that is, it installed fine.
When you were configuring it, something went south, and you decided to re-install it? How did you tried that? Have you been able to re-install it?
Then, you deleted by hand the file "/etc/init.d/bind9", and now you can't re-install bind9?
Is this pretty much what happened? :)

Yes. That is exactly happened. Is there any way I can completely remove BIND from my server? :confused:

---

### Post by hictio on 2010-09-11
Perhaps trying this might help:
```

sudo aptitude reinstall bind9

```

---

