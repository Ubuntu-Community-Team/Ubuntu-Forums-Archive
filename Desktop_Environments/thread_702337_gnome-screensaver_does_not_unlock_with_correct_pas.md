---
title: "gnome-screensaver does not unlock with correct password also"
date: 2008-02-20
forum: Desktop Environments
---

### Post by deepclutch on 2008-02-20
My Debian Sid gnome-screensaver has lock feature enabled.
when running screensaver,if i press the mouse or kbd and give my local user's password for unlocking,it doesnot works :(

I have checked dbus,hal,system-tools-backend etc and all of them are working fine .(can be restarted fine).

I dont know how can I get a backtrace of the application :cry: 

What all services should I check?why do password authentication fails?

---

### Post by deepclutch on 2008-02-20
OK/\ Solved by installing libpam-forefront which is a dependency for gnome-screensaver latest version [IMG]http://linuxquestions.cachefly.net/images/questions/images/smilies/smile.gif[/IMG] also filed a bug report @ Debian BTS :
#383889
#440715

It is Debian Sid which I run ;)

---

