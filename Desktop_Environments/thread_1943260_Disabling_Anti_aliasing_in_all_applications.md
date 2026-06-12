---
title: "Disabling Anti aliasing in all applications"
date: 2012-03-19
forum: Desktop Environments
---

### Post by ziprar on 2012-03-19
Greetings,

I like to know the way to disable Anti aliasing in all applications in Lubuntu.

So far I have tried disabling it from Preferences => Customise feel and look and it worked for most applications, but it did not for VLC and Calibre

Now after some googling I found that Calibre uses QT,  so I installed Qt4-qtconfig, there I found no settings for anti aliasing, then after some more googling I found that anti aliasing is os dependant or something like that and should be disabled in the ubuntu font settings

I then modified 10-antialias.conf in /etc/fonts/conf.avail
```
<edit name="antialias" mode="assign"><bool>false</bool></edit>
```

but it did not do a thing, so now I am stuck, any help is appreciated

Thanks 
Ed

---

### Post by gipsyshadow on 2012-08-11
Hi Ziprar :D
Try [this workaround]("http://ubuntuforums.org/showthread.php?p=12164308#post12164308"). Bye

---

