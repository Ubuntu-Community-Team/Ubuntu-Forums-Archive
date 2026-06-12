---
title: "Domain admin can´t use sudo"
date: 2009-02-26
forum: General Help
---

### Post by Yorkie125 on 2009-02-26
I have successfully joined an installation of Ubuntu Server to a domain. I can log on as a domain admin fine,  but I can´t use sudo as that user.

I have added them to the admin group, but that didn´t work.

I tried manually editing the sudoers file but messed that up so had to restore it!

What I notice is that I log on as DOMAIN\USER but in Users & Groups it displays the user as DOMAINUSER (ie without a slash).

Thanks in advance :)

---

### Post by Xiong Chiamiov on 2009-02-28
Usually, the 'wheel' group is reserved for people allowed to use sudo.  Assuming that's the case on your system, you can add that user to that group like so:
```

sudo usermod -G wheel [username]

```

---

### Post by Yorkie125 on 2009-03-02
Thanks for the reply but that doesn't work; I get "unknown group wheel"

I am using Ubuntu Server if that makes a difference.

---

### Post by Yashiro on 2009-03-02
Run visudo and add yourself/or your group to the sudoers file.

---

### Post by Yorkie125 on 2009-03-02
I found a solution! 

[http://ubuntuforums.org/showpost.php?p=6737332&postcount=9](http://ubuntuforums.org/showpost.php?p=6737332&postcount=9)

editing lwiauthd.conf worked :)

---

