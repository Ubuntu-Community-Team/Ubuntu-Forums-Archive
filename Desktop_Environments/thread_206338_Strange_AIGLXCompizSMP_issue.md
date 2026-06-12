---
title: "Strange AIGLX/Compiz/SMP issue"
date: 2006-06-29
forum: Desktop Environments
---

### Post by magicrobotmonkey on 2006-06-29
Hey, I'm running aiglx and compiz on my inspiron 6400 with the intel integrated graphics, and it runs beautifully. Or it ran beautifully up until a couple weeks ago when I updated some packages and restarted. Then it started running slow. Except when I was compiling something, I was rotating the cube for some reason and noticed it was all smooth again. Until it was done compiling. Then is slowed all down and got choppy again. So I disabled my extra core (echo 0 > /sys/devices/system/cpu/cpu1/online ) and it runs all good again. What gives? Even if I leave them both on  and do yes > /dev/null, it will nail one core and compix will be good again.

So I'm not sure whats going on here. Maybe some layer of the aiglx workings is being indecisive about which processor to use when it has a choice, but I dunno where to start debugging it. Just seems really strange to me. 

Any ideas?

---

### Post by magicrobotmonkey on 2006-07-03
nothing, huh? I might have to start over from a fresh install

---

### Post by fiddler59 on 2006-07-05
There is currently a bug in the i686 kernel as well as smp options. This is a known bug that needs to be resolved in the next kernel update.
DB

---

