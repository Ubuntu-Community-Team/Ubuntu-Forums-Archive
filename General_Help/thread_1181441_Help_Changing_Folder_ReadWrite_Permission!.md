---
title: "Help Changing Folder Read/Write Permission!"
date: 2009-06-07
forum: General Help
---

### Post by LifeEscalade on 2009-06-07
So I'm trying to install No-IP for a host. When i try to make install I keep getting: 
if [ ! -d /usr/local/bin ]; then mkdir -p /usr/local/bin;fi
if [ ! -d /usr/local/etc ]; then mkdir -p /usr/local/etc;fi
cp noip2 /usr/local/bin/noip2
cp: cannot create regular file `/usr/local/bin/noip2': Permission denied
make: *** [install] Error 1

Anyone think they could help me out on this?
Thank you,
LifeEscalade

---

### Post by michy99 on 2009-06-07
you need root permissions.```
sudo make install
```

---

### Post by LifeEscalade on 2009-06-08
i still get the error even when i use sudo. any other suggestions?

---

### Post by michy99 on 2009-06-08
noip2 is in the repositories. Is there any reason you need to compile it from source instead?

---

### Post by H4F on 2009-06-08
May be you don't have enough permission to create file/folders in /usr/local. so again try sudo

---

### Post by LifeEscalade on 2009-06-09
Its all good... i got apache to show the .pl file i was working with and correct permissions now. Now the only thing is that i need help with is the mysql databases the site uses. I havnt been able to find verbose writeups about it. =\ anyone think they could point me to the nearest newb mysql forum?

Much thx,
LifeEscalade

P.S: Take a look for yourself: [http://lolhoomin.hopto.org/wakaba.pl](http://lolhoomin.hopto.org/wakaba.pl)

---

