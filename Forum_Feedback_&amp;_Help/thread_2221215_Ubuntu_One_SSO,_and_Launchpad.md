---
title: "Ubuntu One SSO, and Launchpad?"
date: 2014-05-01
forum: Forum Feedback &amp; Help
---

### Post by hamiljf on 2014-05-01
I'm puzzled by the relationships between Ubuntu One, Ubuntu One SSO and Launchpad.   Some of this may be the result of the Heartbleed bug.  I understand that even when Ubuntu One goes, Ubuntu One SSO will remain.  But my records indicate that I was using SSO to sign on to Launchpad (or possibly, Launchpad to sign on to Ubuntu: I got confused somewhere).  I tried to use the userid and password I had for Launchpad the other day and it did not work: I assumed because they'd binned everything as a result of Heartbleed.  But now I find the same userid and password still work for Ubuntu forums, etc.  Can someone explain the relationship between SSO and Launchpad ?
I value Ubuntu.  I value Ubuntu SSO.  14.04 is good (except for the common complaint about editting the launcher buttons).  I'm happy that is it now possible to correct profile errors without having first become a guru.

---

### Post by Irihapeti on 2014-05-01
*Thread moved to **Forum Feedback & Help**.*

Not about Ubuntu One file sync.

---

### Post by Jon Hanna on 2014-05-01
From [http://blog.canonical.com/2014/04/02/shutting-down-ubuntu-one-file-services/](http://blog.canonical.com/2014/04/02/shutting-down-ubuntu-one-file-services/)

> The shutdown will not affect the Ubuntu One single sign on service, the  Ubuntu One payment service, or the backend U1DB database service.

---

### Post by Jon Hanna on 2014-05-01
From [http://blog.canonical.com/2014/04/02/shutting-down-ubuntu-one-file-services/](http://blog.canonical.com/2014/04/02/shutting-down-ubuntu-one-file-services/)

> The shutdown will not affect the Ubuntu One single sign on service, the  Ubuntu One payment service, or the backend U1DB database service.

SSO certainly seems to have been working of late too, including on launchpad.

---

### Post by bapoumba on 2014-05-01
To log into Launchpad, you use the same email/password you use to login Ubuntu-One SSO.

---

### Post by hamiljf on 2014-05-01
Thanks for these replies.  Symptom was that I tried to use my Launchpad sign-on to access another service and it got bounced, apparently by Launchpad.  I was just able to sign on to Launchpad directly, so I suppose the earlier failure was some sort of glitch.  Is the OpenID (?) 'owned' by SSO and used by Launchpad or 'owned' by Launchpad and used by SSO ?

---

### Post by bapoumba on 2014-05-01
[https://help.launchpad.net/YourAccount/OpenID](https://help.launchpad.net/YourAccount/OpenID) ?
Not sure as I do not use LP OpenID.

Maybe you could use Ubuntu One SSO as an OpenID [https://help.ubuntu.com/community/SSO](https://help.ubuntu.com/community/SSO) ?

---

