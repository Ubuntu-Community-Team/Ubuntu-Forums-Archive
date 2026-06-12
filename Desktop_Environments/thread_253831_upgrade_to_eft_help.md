---
title: "upgrade to eft help"
date: 2006-09-08
forum: Desktop Environments
---

### Post by nephish on 2006-09-08
i have a quick question about an upgrade scenario. 
could i update from dapper to knot2 by altering the sources in /etc/apt/sources.list to the edgy release then
```
apt-get update
apt-get dist-upgrade
```

is this ok, or will it break my system big time ?

thanks

---

### Post by enopepsoo on 2006-09-08
I have been afraid to try it because I am a big scaredy as well.  Someone please let us know.

We appreciate your assistance.:D

---

### Post by jISh on 2006-09-08
I haven't tried it but I will tell you that clean installs are always a much better option.


Move your /home folder to a seperate partition or back up your data and wipe the rest, I say.

---

### Post by enopepsoo on 2006-09-08
I will just wait, honestly it is only a month and a half.  I don't need the hastle. 

I am getting a new comp in a week.  This one *might*  become a webserver or something like that, but I have no need to do weird upgrade stuff now.

---

### Post by powder on 2006-09-09
If it's going to be a server, dapper will probably be more stable than edgy anyway.

---

### Post by the-linux-guy on 2006-09-09
> **nephish said:**
> could i update from dapper to knot2 by altering the sources in /etc/apt/sources.list to the edgy release then
```
apt-get update
apt-get dist-upgrade
```
is this ok, or will it break my system big time ?

I tried it yesterday, took it even easy by upgrading not to many things at a time. It went rather well until 75% of my installed packages was succesfully upgraded, and all of the sudden... yes, my system broke big time ! :( 
I wouldn't recommend upgrading your dapper to edgy, too much things are changed and due to a changed c-library, dapper packets become no longer compatible with the edgy ones...

---

### Post by nephish on 2006-09-09
well thanks for the lesson learned. I will do it the long way and back up everything and go from scratch. whew.

appreciate it, sorry about your crash though.

---

### Post by max.diems on 2006-09-09
DON'T UPGRADE YET! The wait until the final release is less than two months.

---

