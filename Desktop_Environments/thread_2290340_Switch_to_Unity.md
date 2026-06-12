---
title: "Switch to Unity"
date: 2015-08-11
forum: Desktop Environments
---

### Post by Eslar on 2015-08-11
Hi there, 

I'm running Ubuntu 15. 04 with GNOME3
```
lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

```
I've been wanting to try out the Unity DE but no matter what I try, I can't seem to get the option in the login screen. 
I've apt-get installed unity and ubuntu-desktop, are there any additional steps I am missing? 
Cheers

---

### Post by deadflowr on 2015-08-11
If there is no option at login, then you might not have installed the ubuntu-session package.
The session name at login, though, will be ubuntu and not unity, fwiw.

---

### Post by ajgreeny on 2015-08-11
How did you add unity to the OS?

You probably need to install **ubuntu-desktop** package if you want the full Ubuntu system with unity.

---

### Post by Eslar on 2015-08-13
Many thanks to the both of ye, 

ubuntu-session was indeed what I was missing, and after installing that I was able to switch DEs. On a different note however, I'm not sure if Unity is in fully functionality at that. Further research is needed

Also thanks to whomever moved this thread to the appropiate DE category, my apologies for not doing it in the first place

---

