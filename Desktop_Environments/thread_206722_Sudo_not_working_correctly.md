---
title: "Sudo not working correctly"
date: 2006-06-30
forum: Desktop Environments
---

### Post by Simian on 2006-06-30
I rebooted the yesterday for the first time in ages. But when I did I had network problems. I looked in /etc/hosts and it had my host name and 127.0.1.1 all over the screen (perhaps 20-30 times). I fixed that but now when I try to sudo anything from the command line it says:
```
sudo: unable to lookup sunshine via gethostbyname()
```
but it still executes the command correctly though.
But if I try to run an app from the desktop that requires root priverlages it just doesn't run.

I really need some advice :)

---

### Post by jarland on 2006-06-30
Try this thread, see if it helps.

[http://www.ubuntuforums.org/showthread.php?t=176300](http://www.ubuntuforums.org/showthread.php?t=176300)

---

### Post by invalid on 2006-06-30
[QUOTE=Simian]I rebooted the yesterday for the first time in ages. But when I did I had network problems. I looked in /etc/hosts and it had my host name and 127.0.1.1 all over the screen (perhaps 20-30 times). I fixed that but now when I try to sudo anything from the command line it says:
```
sudo: unable to lookup sunshine via gethostbyname()
```
but it still executes the command correctly though.
But if I try to run an app from the desktop that requires root priverlages it just doesn't run.

I really need some advice :)[/QUOTE]
[http://ubuntuforums.org/showpost.php?p=1045047&postcount=3](http://ubuntuforums.org/showpost.php?p=1045047&postcount=3)

---

### Post by wylfing on 2006-06-30
I think **invalid** has it. Your /etc/hosts file is messed up, so when it tries to look you up by machine name it can't do so. Patch up your hosts file like it says in the linked post and you should probably be fine.

A good lesson here is whenever you mess with system configuration files, you should always, *always* back them up first.

:)

---

### Post by Simian on 2006-06-30
Thanks guys for your quick replies. That did the trick :)

---

