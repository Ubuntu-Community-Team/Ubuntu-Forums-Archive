---
title: "locked out of nautilus &amp; system"
date: 2010-09-01
forum: Desktop Environments
---

### Post by lumore22 on 2010-09-01
Greetings-

Dual boot sys with ubuntu lucid lynx 10.04 on Windows 7 host.

I created a dot directory (.rams) yesterday and decided to do a chmod on it. **Stupidly,**(you can call me a moron) I used the asterisk as a shortcut notation and in effect chmod-ed all the dirs starting with a dot. So when I tried to login, this AM,an error mesg appeared that advised me to change the permissions but I could not get into a console or the desktop. After trying several things on Windows, I simply moved the exisitng ubuntu install into another folder, ran uninstall and re-installed.  

But is there any way that I can access the sys to undo my stupidity? I have a ton of docs on this install.

Any suggestions would be helpful.

Thanks in advance!:sad:

---

### Post by kpkeerthi on 2010-09-01
Boot with the Live CD. Mount the partition where your . (dot) folders exist and reverse the chmod.

---

### Post by lumore22 on 2010-09-02
Thanks. I tried that but couldn't . I think its because grub?? was seeing an already existing install of ubuntu. The cd was recognized only after I did the uninstall. And that was from Windows. I will try again. 

Regards
:KS

---

### Post by VanillaMozilla on 2010-09-03
Just choose recovery mode from grub and log in from there.  Although if you uninstalled, you've probably really destroyed it by now.

---

