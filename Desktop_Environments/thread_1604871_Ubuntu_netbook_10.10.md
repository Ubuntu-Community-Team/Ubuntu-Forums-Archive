---
title: "Ubuntu netbook 10.10?"
date: 2010-10-24
forum: Desktop Environments
---

### Post by mrwoody on 2010-10-24
Sorry for the basic question, but how do I know if I installed the
netbook version of ubuntu or the vanilla version on my dell mini 10? 

I was sure that I downloaded the .iso for the netbook version, but I seem to get the normal ubuntu.

---

### Post by Manshtein on 2010-10-24
hi!

may be /etc/lsb-release contains info you looking for?

---

### Post by mrwoody on 2010-10-24
> **Manshtein said:**
> hi!

may be /etc/lsb-release contains info you looking for?


Thanks for the advice:

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

```

Looking around, it seems to me that I installed vanilla Ubuntu. 
Is there an easy way to switch or shall I just re-install the whole thing again?

---

### Post by Manshtein on 2010-10-24
looking deeper in netbook remixes i have found, following command --

sudo apt-get install ubuntu-netbook-remix

---

### Post by mrwoody on 2010-10-24
> **Manshtein said:**
> looking deeper in netbook remixes i have found, following command --

sudo apt-get install ubuntu-netbook-remix

is the new version of ubuntu netbook 10.10 the same as netbook-remix? 
I thought that they were not. But since I don't have alternatives at the moment, I will give it a shot! 

Thanks!

**Edit:** I just realized that ubuntu-netbook-remix does not exist anymore. I think it has been replaces with ubuntu-netbook, and I have that installed. So I suppose mine is the right version. 
My question now is, how to get the pretty stuff shown at:
[http://www.ubuntu.com/netbook/features](http://www.ubuntu.com/netbook/features)

---

### Post by Manshtein on 2010-10-24
Actually i do not know differences between regular and netbook ubuntu releases except desktop view. :) 

Here is topic i have found regarding that command -- 

[http://ubuntuforums.org/showthread.php?t=1211299](http://ubuntuforums.org/showthread.php?t=1211299)

Regarding latest post, i am using X-window just for internet and have no idea how to switch themes.

---

### Post by Manshtein on 2010-10-24
Here is one more topic about ubuntu netbook release

[https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)

May be it will help you!

---

### Post by mrwoody on 2010-10-24
> **Manshtein said:**
> Here is one more topic about ubuntu netbook release

[https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)

May be it will help you!

thanks very much for your help. 

I found the problem. Ubuntu didn't like my graphic card (GMA 500) and it wouldn't start the netbook version without its drivers. 

I installed the drivers, and now it is so slow that it is unusable. 
At least I know where to look now! ;-)

---

### Post by mrwoody on 2010-10-24
This is the reason why it is not working:

[http://code.google.com/p/gma500/issues/detail?id=39](http://code.google.com/p/gma500/issues/detail?id=39)

Thanks again for your help!

---

