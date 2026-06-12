---
title: "how to make apt / dpkg ignore errors?"
date: 2004-12-30
forum: Desktop Environments
---

### Post by negativ on 2004-12-30
In an attempt to fix a postfix problem, I decided to try to remove it and reinstall it.

however, when I try
```
$ sudo apt-get remove postfix
```

it tries to stop postfix, then fails because postfix isn't running.  Thereafter , it refuses to remove the package because of the failure to stop a service which isn't started in the first place.

You might be thinking, well, why not just start postfix and let apt stop it?  WELL THAT'S THE PROBLEM IN THE FIRST PLACE!!  POSTFIX WON'T START.  It says it's started, but it isn't. 

So, how can I get apt or dpkg to ignore this error and just remove the freakin' package already?

---

### Post by Rancoras on 2004-12-30
Try
```
sudo apt-get install --reinstall postfix
```

---

