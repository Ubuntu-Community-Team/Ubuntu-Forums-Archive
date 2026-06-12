---
title: "kopete: icq client too old"
date: 2006-07-31
forum: Desktop Environments
---

### Post by vidak on 2006-07-31
When connecting to ICQ through kopete, I get a message, that my client is too old - which I can't believe, since I got the latest (0.12.1) version of kopete... I remember I had once a problem like that, but I can't remember how I solved it...
Any ideas?

---

### Post by r0nin on 2006-08-01
I have the same problem too after updating Kubuntu!

---

### Post by Kurt` on 2006-08-01
It's not that YOUR client is out of date, the ICQ server is expecting your client to report a certain version # to it (say, "50"), and your client is reporting an old version (say, "49").

I don't use Kopete, but if you can configure the version # in your options, please do so. :o

---

### Post by r0nin on 2006-08-01
> **Kurt` said:**
> It's not that YOUR client is out of date, the ICQ server is expecting your client to report a certain version # to it (say, "50"), and your client is reporting an old version (say, "49").

I don't use Kopete, but if you can configure the version # in your options, please do so. :o

Does anyone know how to do that? I didn't find anything in the settings.

---

### Post by r0nin on 2006-08-01
Download the proper [deb](http://kubuntu.org/~jriddell/kopete/) and install. Works perfectly for me.

---

### Post by Aldoo on 2006-08-01
Hi ! Those were patched 0.12.0 kopete packages.

Don't you have the latest version (0.12.1) with the patch for the new ICQ protocol ?

---

### Post by r0nin on 2006-08-01
I didn't make those debs. They are official unofficial Kubuntu debs.

---

### Post by colo on 2006-08-01
So why the hell are they built against KDE 3.5.3, while Kubuntu 6.06 "Long Term Support Blah" sports 3.5.2?

---

### Post by ps- on 2006-08-01
because the "official unofficial" kde packages for dapper are 3.5.3:
[http://kubuntu.org/announcements/kde-353.php](http://kubuntu.org/announcements/kde-353.php)

but i agree: such patches should be backported to dapper and go into dapper-updates

---

