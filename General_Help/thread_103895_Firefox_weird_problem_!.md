---
title: "Firefox weird problem !"
date: 2005-12-15
forum: General Help
---

### Post by DarkAngel88 on 2005-12-15
Hi there,

First time poster here, I've been reading you since a while and I found most of the info needed here, thanks to all the ubuntu experts helping this communauty ! :) 

But this time, I got a weird looking problem with firefox 1.5.  The thing is that after a fresh install I get firefox running without any problem.  I installed all my extensions and start customizing Firefox.  After, let say 5-10 startup, I get a different firefox from the version I'm used to work with.  For example, I can't use the google search box..all I get is a magnifying glass and I cannot add any search engine.  I looked on the forum and tried the few examples how to get it back without any success.  Also, I always lose my saved session (saved with Tabmixplus).  I don't lose my extensions or my bookmarks but everything else I customize before.  I tried different ways to get my settings back like reinstalling Firefox using the wiki page without any success.  Even tried a firefox script here but I still got the same problems...  First it works... and then, after like 10 minutes of closing and restarting firefox (for test issues), I get this annoying problem.

Now... I'm quite sure I'm not the only one with this problem.  Looks like a permission problem to me but hey.. it's only been 1 week since I use ubuntu.  I really like this distro, but I found this problem really annoying :???:  If someone can help me I'll be greatfull !!

PS : Sorry for my english... it's not my native language !

---

### Post by towsonu2003 on 2005-12-15
a quick fix if it's a permissions problem: ```
cd
chown -R username:username .mozilla/
chmod -R u+rw .mozilla/
``` If you get any errors, copy them here... chown will change the owner of all the files+folders (-R) under .mozilla to username (put your own instead) and chmod will make all files+folders (-R) under .mozilla to be readable and writable to username (change username with your own) (u+rw means user will have read and write permissions). 
hope this will help. .mozilla (under /home/username/) is the folder where firefox keeps its setting.

---

### Post by DarkAngel88 on 2005-12-15
Hi towsonu2003, 

Thanks for you quick answer.. I tried what you have told me but it seems it doesn't work.  I still get the same problem with firefox.

If anyone allready had this problem.. please help me !

Thanks !

---

### Post by gnr259 on 2006-05-11
Hey,

   I had a similar problem couldnt even bookmark a webpage ](*,)  ... 
I did this simple thing to get my firefox back ... but this is only when u dont want settings to be preserverd ...

===================
close all the instances of firefox

rm -rf ~/.mozilla

restart firefox things will work fine !!!
=================

---

### Post by towsonu2003 on 2006-05-11
[QUOTE=gnr259]
===================
close all the instances of firefox

rm -rf ~/.mozilla

restart firefox things will work fine !!!
=================[/QUOTE]
moving firefox might be a better idea:
```

#close firefox
mv ~/.mozilla/firefox ~/firefox-broken
#restart firefox, your old files (cookies, bookmarks and so on) are now in /home/username/firefox-broken
```

---

