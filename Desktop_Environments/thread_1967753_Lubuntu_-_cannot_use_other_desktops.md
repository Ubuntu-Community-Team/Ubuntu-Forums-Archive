---
title: "Lubuntu - cannot use other desktops"
date: 2012-04-28
forum: Desktop Environments
---

### Post by 23senick on 2012-04-28
Two questions here, the first is the principal one though advice on the second could make the first irrelevant

I have 2 machines with Lubuntu, one a minimal install, the other standard. I can't get xfce desktop to work on either. At log in I select xfce session but just get returned to the log in screen.  Any ideas why?  I used the meta package and synaptic doesn't show any dependency issues.  

The reason I installed xfce is I understand lxde won't be LTS even in 12.04. One of the machines has an SSD so I want to stick with the LTS to reduce the number of re-writes to the SSD.  Is the only option a fresh xubuntu install?  

I posted this question before and was told I had "directed it wrongly." Hoping someone out there has some advice which is a bit more helpful....

---

### Post by grahammechanical on 2012-04-28
I do not think that putting the XFCE user interface on to Lubuntu will turn Lubuntu into an LTS release.

Underneath it will still be Lubuntu. Surely. It is the underneath parts that are supported with security fixes for 18 months.

Regards.

---

### Post by IWantFroyo on 2012-04-28
I agree with grahammechanical. You need the core of the system.

Xubuntu 12.04 is still only supported until 2015. If you want the 5 year support, I recommend installing the server version of Ubuntu, and installing LXDE from there.

Links:
[https://wiki.ubuntu.com/Xubuntu](https://wiki.ubuntu.com/Xubuntu)
[http://www.ubuntu.com/download/desktop/alternative-downloads](http://www.ubuntu.com/download/desktop/alternative-downloads)

---

### Post by 23senick on 2012-04-28
Thanks, that's helpful. Still not sure why I can't add different desktop environment to Lubuntu...

---

### Post by Herpythebrony on 2012-04-28
> **23senick said:**
> Thanks, that's helpful. Still not sure why I can't add different desktop environment to Lubuntu...
Try this.

```
sudo apt-get install numlockx parcellite
```

---

### Post by 23senick on 2012-04-29
Thanks [Herpythebrony]("http://ubuntuforums.org/member.php?u=1608717") but didn't seem to do anythin. However I just upgraded the pc with standard Lubuntu to 12.04...and xfce works now!

Will try the netbook with minimal install when I get the time...

---

