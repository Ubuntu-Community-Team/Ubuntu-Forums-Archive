---
title: "GDM freezes and logout"
date: 2005-05-01
forum: Desktop Environments
---

### Post by diego on 2005-05-01
Greetings,

I'm working on getting Ubuntu up 'n running on a Amd64 notebook for a week now and the problem is:

Everytime I login usgin GDM it gets me to an "Ubuntu brown" empty screen and it freezes there for 10 seconds or so and then it comes back to gdm. 2nd time I login works perfectly  :? 

Some info: I compiled the nvidia module using make-kpkg and I'm running 2.6.11-amd64-k7, only Hoary packages.

Any idea anyone?

---

### Post by Alexander Kirillov on 2005-05-02
[QUOTE=diego]Greetings,

I'm working on getting Ubuntu up 'n running on a Amd64 notebook for a week now and the problem is:

Everytime I login usgin GDM it gets me to an "Ubuntu brown" empty screen and it freezes there for 10 seconds or so and then it comes back to gdm. 2nd time I login works perfectly  :? 

Some info: I compiled the nvidia module using make-kpkg and I'm running 2.6.11-amd64-k7, only Hoary packages.

Any idea anyone?[/QUOTE]
 Any error messages in ~/.xsession-errors or in /var/log/ Xorg.0.log ?

---

