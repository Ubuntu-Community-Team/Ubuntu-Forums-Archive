---
title: "Install nvidia beta drivers - aiglx - beryl on ubuntu 6.06"
date: 2006-10-05
forum: Desktop Environments
---

### Post by FuzZy2006 on 2006-10-05
Can anybody tell me how can i install the nvidia beta drivers to be able to use aiglx + beryl?

---

### Post by bristi on 2006-10-05
Please search the forums. A quick search led me to this:
[http://www.ubuntuforums.org/showthread.php?t=263851&highlight=aiglx+nvidia+beryl]("http://www.ubuntuforums.org/showthread.php?t=263851&highlight=aiglx+nvidia+beryl")

 Which should be exactly what you (and I) need :)

---

### Post by FuzZy2006 on 2006-10-05
thx, but it says that it is for edgy eft. does it work on dapper?

---

### Post by Aualin on 2006-10-05
No it doesnt, the repos are for edgy...
But it arent so hard, i got beryl on dapper...
I first instaleld from nvidias script, and added repos. Then i run
```
apt-get build-dep beryl
apt-get build-dep beryl-core
apt-get build-dep beryl-plugins
apt-get build-dep beryl-manager
apt-get build-dep beryl-settings
apt-get build-dep emerald
apt-get build-dep emerald-themes
```
And then i run
```
svn co http://svn.beryl-project.org/trunk/
```
in home directory not root!
and then i
```

cd trunk
sudo ./makeall

```
and when it finished making them i run
```
beryl-manager
```

Here is a guide thats hopefully more clear than my fast guide :p 
[http://forum.beryl-project.org/topic-4697-howto-build-beryl-dapper](http://forum.beryl-project.org/topic-4697-howto-build-beryl-dapper)

---

