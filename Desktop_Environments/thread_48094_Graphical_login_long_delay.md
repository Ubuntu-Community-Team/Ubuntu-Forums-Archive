---
title: "Graphical login long delay"
date: 2005-07-11
forum: Desktop Environments
---

### Post by blueturtl on 2005-07-11
I've created a new user for my partner under Ubuntu using the System menu->Administration->Users and Groups and we have the following problem: whenever she logs in using her own username it takes ages (read 5 minutes or more) before she can reach her desktop. During this time there seems to be no disk activity or any other activity either. The Ubuntu splash appears and it's caught on the Session Manager Proxy. The system is not locked up, but she thought it was (and being a Windows user reset my computer two times)  [-X  I'm a bit dumfounded with this one, as I have no idea what could cause it. If she logs in through a command prompt terminal there is no delay whatsoever so I'm assuming it must be a Gnome problem. However I do not know why my username does not suffer from this same issue. Any assistance would be greatly appreciated.

---

### Post by Joeb on 2005-07-11
Look in the .gnome2 directory in her home directory and delete the session file located there and see if that fixes the problem.

---

### Post by blueturtl on 2005-07-11
It did indeed fix the problem. What might have caused this? How do I avoid it in the future? And of course thank you for your time.  ;-)

---

### Post by Joeb on 2005-07-11
[QUOTE=blueturtl]It did indeed fix the problem. What might have caused this? How do I avoid it in the future? And of course thank you for your time.  ;-)[/QUOTE]


I'm not sure what might have caused it.  I only know that when I have done something that messes up the saved session, it takes forever to load gnome.  That doesn't mean that you did anything to mess up the session, just that the session was in a state it couldn't restore from and had to eventually error out before proceeding.

I'm glad it worked, though.

JoeB

---

