---
title: "Problem upgrading to Oneiric"
date: 2011-10-13
forum: Desktop Environments
---

### Post by Luke Kijanovich on 2011-10-13
Today I upgraded to Oneiric and now I can't login, although I can login using guest account. I believe that lightdm is crashing. I'm sorry for the lack of information, if you need other info, I will post it.

---

### Post by neu5eeCh on 2011-10-13
You're using Xubuntu? So am I. 

I was just going to ask others whether it's possible to upgrade in Xubuntu. I know that in other distros (based on Ubuntu) using the "Ubuntu" upgrade can seriously muck things up. That's all I can tell you for now.

---

### Post by Toz on 2011-10-13
It might be possible that you have been affected by this bug: [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/871667]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/871667").

Can you Ctrl+Alt+F1 to go to a vt and login at the text screen there. Type in the following command:
```
cat ~/.xsession-errors | grep -i xauthority
```and if you get back a reply with some text about "permission denied", the fix appears to be:
```
rm ~/.Xauthority
```
...then Ctrl+Alt+F7 and login.

EDIT: In the event you get an error deleting the .Xauthority file because you don't have permission, try the following:
```
cd
sudo rm .Xauthority
```

---

### Post by Luke Kijanovich on 2011-10-17
I've "fixed" problem by switching back to gdm. I didn't like lightdm too much anyway. Thanks anyway.

---

