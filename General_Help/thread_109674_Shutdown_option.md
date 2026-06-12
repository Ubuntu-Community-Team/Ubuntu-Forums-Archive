---
title: "Shutdown option"
date: 2005-12-29
forum: General Help
---

### Post by noeluylee on 2005-12-29
Hi, I install the KDE on top of Ubuntu. 

I notice that there's no shutdown option. Can you guys point me what to do? :)

Thanks a lot.

Noel

---

### Post by Rinzwind on 2005-12-29
I have one :P It's on the lower part of your k-menu.

edit: Come to think of it: it has "end session" in it.
That logs you off and in the splash screen where you type login-in name and pwd you have a "session" button that has shutdown in it.

---

### Post by noeluylee on 2005-12-29
Its on the Log Out? when I click it, I just see End Current Session and Cancel =(

---

### Post by Rinzwind on 2005-12-29
Yes, take end current session. Then you log off from kde and get another screen where you can log in and can shutdown.

---

### Post by noeluylee on 2005-12-29
Got the solution.. You have to install the kdm...

Run:
sudo dpkg-reconfigure kdm

TY.. :)

---

### Post by adie273 on 2005-12-29
You have to use KDM rather than GDM. Otherwise the shutdown option doesn't appear in KDE.

(Although i found it does appear no matter what, in KDE 3.5. Whether thats just me i dunno)

Adie

---

