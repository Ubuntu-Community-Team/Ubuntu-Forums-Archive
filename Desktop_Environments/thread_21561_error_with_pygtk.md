---
title: "error with pygtk"
date: 2005-03-22
forum: Desktop Environments
---

### Post by wanama on 2005-03-22
Hi to all!! I'm a new ubuntu-logic man and i want to say that the true value of this distro is the wonderful community behind... And now the question. I can't understand why i get a big error when i launch the gnome-app-install (the same is for the Ubuntu-Update-Manager). Since i've installed python2.3 form source i can't loaunch anymore these apps. I've done an apt-get dist upgrade for just 35 packets but the problem still here. Don't know is thi issue is about some broken package but apt-get seems without problems. Maybe some simlink broken after the python2.3 install? Please help guyz..... heres' the code:
```
root@machine:/home/andrea # gnome-app-install
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 21, in ?
    import pygtk; pygtk.require("2.0")
ImportError: No module named pygtk
root@machine:/home/andrea # update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 25, in ?
    import pygtk
ImportError: No module named pygtk
root@machine:/home/andrea #
```

---

### Post by wanama on 2005-03-22
Don't mind i've fixed now!...it was a problem of simlinks... if someone has my same problem please post here and 'ill tell the solution...    :mrgreen:

---

### Post by gui on 2005-07-14
If your proposition is still up, I'm interested!

I'm trying to run tinyerp on my PC. the server side is up, But I can't get the client working. I've got the same error you had :

Traceback (most recent call last):
  File "./tinyerp-client", line 55, in ?
    import pygtk
ImportError: No module named pygt

---

### Post by gui on 2005-07-15
up

 ](*,)

---

### Post by rwabel on 2005-07-23
I'm also intersted, I've the same problem with griffith

---

### Post by Casagrande on 2005-07-25
i have the same problem
i stalled the last ubuntusetup-sh and python 2.3
and now  :-( 
can somebody help me, i am beginner

---

### Post by rwabel on 2005-07-25
I had the problem when I wanted to start BloGTK. In that case I changed the line
```
#!/usr/bin/env python
```
to
```
#!/usr/bin/env python2.4
```

it seems that BloGTK uses the wrong version of python.

Maybe this helps for some people.

---

### Post by Casagrande on 2005-08-09
not solution
can perhaps somebody help?
thanks

---

