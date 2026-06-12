---
title: "why doesnt compiz work?"
date: 2007-10-25
forum: Desktop Effects &amp; Customization
---

### Post by jacob01 on 2007-10-25
i installed the comiz configure program and i have tried to activate the effects but when i try to enable the effects my computer screen looses the window boarder and then come up with an erro saying i cant or that their is an error. i checked if direct render is enabled and it is, so i ran dlx gears i i can run that pretty smooth. whats the problem.  ni have run compiz and beryl on this same computer so it can run it.

---

### Post by 444 on 2007-10-25
Open the Terminal and type in "compiz", that way you'll see the exact error.

---

### Post by jacob01 on 2007-10-25
ok this is the out put

```
jacob@jacob-desktop:~$ compiz
Checking for Xgl: not present. 
Blacklisted PCIID '8086:29a2' found 
aborting and using fallback: /usr/bin/metacity
```

ok so it looks to me that i need the xgl code, snd it is not my graphics card. correct me if im wrong.

---

### Post by 444 on 2007-10-25
Nah, it's the blacklisting causing the hangup. Apparently it disabled the video player or something so they disabled it for that Intel graphics by default.

[http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)
[https://bugs.launchpad.net/ubuntu/+bug/140833](https://bugs.launchpad.net/ubuntu/+bug/140833)

---

