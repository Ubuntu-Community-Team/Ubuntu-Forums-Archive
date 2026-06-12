---
title: "problem with hibernate"
date: 2012-02-26
forum: Desktop Environments
---

### Post by forsubhi on 2012-02-26
I am facing the following problem during hibernate

hibernate:Warning: Tuxonice binary signature file not found.

[IMG]http://s15.postimage.org/xedg5ts57/Screenshot_at_2012_02_27_06_37_45.png[/IMG]

---

### Post by musicman10489 on 2012-02-29
Maybe you need to install these packages? 
```
linux-generic-tuxonice
linux-headers-generic-tuxonice
```

If nothing else, this might be a good starting place.
[https://help.ubuntu.com/community/PowerManagement/Hiberate#TuxOnIce](https://help.ubuntu.com/community/PowerManagement/Hiberate#TuxOnIce)

---

### Post by forsubhi on 2012-03-10
[SIZE=3]I try [/SIZE][SIZE=3]uswsusp ,the hibernate process work well,but after I hibernate the pc and when I power it again the pc hang on start up and nothing response until I restart it [/SIZE] [B]
[/B]

---

### Post by jbernardo on 2012-04-23
Are you on 12.04?
Hibernate has been disabled by default in ubuntu. You need to edit a obscure policy file to get it to work. See the discussion [here]("http://www.ubuntuvibes.com/2012/04/hibernation-disabled-by-default-in.html") and the "bugs" [here]("https://bugs.launchpad.net/ubuntu/+source/policykit-desktop-privileges/+bug/812394") and [here]("https://bugs.launchpad.net/ubuntu/+source/kde-systemsettings/+bug/976654").

---

### Post by fara on 2012-04-23
> **jbernardo said:**
> Are you on 12.04?
Hibernate has been disabled by default in ubuntu. You need to edit a obscure policy file to get it to work. See the discussion [here]("http://www.ubuntuvibes.com/2012/04/hibernation-disabled-by-default-in.html") and the "bugs" [here]("https://bugs.launchpad.net/ubuntu/+source/policykit-desktop-privileges/+bug/812394") and [here]("https://bugs.launchpad.net/ubuntu/+source/kde-systemsettings/+bug/976654").

thanks jbernardo, I was wondering about that. tried 
```
sudo pm-hibernate
```

it worked with no problem, so i'm getting my hibernate option back.

cheers

---

