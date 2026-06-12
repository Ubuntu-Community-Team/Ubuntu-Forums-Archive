---
title: "The AltGr isn't working anymore"
date: 2006-02-08
forum: Desktop Environments
---

### Post by windmill on 2006-02-08
Hello,

I replace this message here, I first post it wrongly under 'ubuntu' forums.

Since a while, but I can't remember since when, I can't use my Alt Gr key anymore (usefull for at brackets and terminals...)
I can't use them neither in terminal neither in applications such as Kile or others.
In fact, I can use the altgr sometimes but then (for  an unknown reson) it isn't possible anymore, it's like it has been transformed to the ctrl (when I scroll with my mouse it zooms in my documents...)
I googled the net on this issue (and it often comes up ) but didn't find an answer which could help me. There is a lot of talk about XF86 but I don't have those files on my PC !!
I also use nx-client from nomachine with freenx but I don't think this is the problem (no documentation on this on the web)

I don't know what to do anymore -- please help!


I'm running the latest  kubunutu (3.5.1) version (but there is no difference under gnome)

Could it be that the problem comes from the 3.5.1 KDE upgrade ?
Which files do I need to check for an error ?
Thank you

---

### Post by windmill on 2006-02-08
To be a bit more precise :

It is acting as a control key when working under kate or kile but it is effective when I work under Write Open office !!!

Please help....

---

### Post by Goochi on 2006-02-12
I have the same problem.

I've been on Ubuntu for a year and a half with this keyboard. And one day I bounced upon this issue. I even formatted in a last attempt to fix, but that DIDN'T do it. Which seems reaaaally weird to me. I just format, got on my X server, and still no ALT GR. spooky no? :p

Any help is welcome.
Thanks,
gOochi

---

### Post by Neo Ex on 2006-02-12
Simply run 'sudo ln -s /etc/X11/xkb /usr/share/X11 ' and log out and re-login.

---

### Post by Goochi on 2006-02-15
Your 'simply' command didn't do it for me.

But thanks for the attempt..

---

### Post by mansie on 2006-10-22
> 
Simply run 'sudo ln -s /etc/X11/xkb /usr/share/X11 ' and log out and re-login.

Worked great for me, thanks for the tip.

Note you prolly need 'sudo rm -rf /usr/share/X11/xkb' first, then after that you can  'sudo ln -s /etc/X11/xkb /usr/share/X11'

Cheers

```

sudo rm -rf /usr/share/X11/xkb
sudo ln -s /etc/X11/xkb /usr/share/X11

```

---

