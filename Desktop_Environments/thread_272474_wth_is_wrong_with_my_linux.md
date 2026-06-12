---
title: "wth is wrong with my linux?"
date: 2006-10-06
forum: Desktop Environments
---

### Post by tiberius147 on 2006-10-06
asunderlin@asunderlin-desktop:~$ su
Password:
su: Authentication failure
Sorry.
why do i not have the permition to do stuff on my own comp
i cant even save stuff inyware nor can i edit the sources.list wich has an error so i need to fix it.
I went in to users and groups and all privlages are checked but i get this when installing java
asunderlin@asunderlin-desktop:/usr/lib/mozilla-firefox/plugins$ ln -s home/asunderlin/Desktop/jre1.5.0_06/plugin/i386/ns7/libjavaplugin_oji.so
ln: creating symbolic link `./libjavaplugin_oji.so' to `home/asunderlin/Desktop/jre1.5.0_06/plugin/i386/ns7/libjavaplugin_oji.so': Permission denied
asunderlin@asunderlin-desktop:/usr/lib/mozilla-firefox/plugins$
i am the only user on the comp wtf!!!!!](*,)

---

### Post by pstewart on 2006-10-06
As far as I know, the su command will only work if the root account is enabled, which it isn't by default in Ubuntu.

Try using sudo instead and entering your normal password.

Hope that helps,
Pete

---

### Post by pstewart on 2006-10-06
This explains the difference between su and sudo better than I can. :)
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by talrasha on 2006-10-06
Yup that's right. root account was disabled by default in ubuntu so  you can't use the su command. try using sudo then the command you want to execute

e.g.
$sudo mkdir

If you want to enable root account to use the su command follow the steps here [http://www.ubuntuguide.org]("http://www.ubuntuguide.org")

---

### Post by lkagan on 2006-10-06
Mac OS X was the first *nix operating system that I used that disabled the root account.  It pissed me off and I always enabled it right after an install.  Then Ubuntu did it and I did the same thing, enabled the root account.  As of recently, I've been using sudo for security reasons.  It's a bit more work especially when you're trying to edit a file that is only visible to root.  You would type something like 

```

sudo vi /etc/sha<tab>

```

And expect the rest of the file name to be displayed, but since you're not root **while issuing** the command, you have to type out the full name.

Anyway, try to use sudo.  If it gets to be too much of a pain, use 

```

sudo passwd root

```

That will set the password for root to whatever you want end then you'll be able to su to root.

Larry Kagan

---

### Post by wenzlicker on 2006-10-06
You can always type sudo su. When you do that you get a root terminal so you don't have to type sudo every time.

```
sudo su
```

---

