---
title: "Gnome panel notification area render mess"
date: 2010-12-09
forum: Desktop Environments
---

### Post by foomor on 2010-12-09
I run ubuntu 10.10 x86_64 and have a strange notification area icons render issue. Sometimes it's fine, but more often it's messed up. Here is an example i've caught right now:

[IMG]http://i.piccy.info/i5/51/09/820951/Screenshot.png[/IMG]

It is not actually the most worst look :D

Anyone had/has something like that? I suppose to think it is a video system issue, i have intel gma4500.

---

### Post by Krytarik on 2010-12-09
It seems to be a common problem, I also had it once, in my case I thought it had something to do with logging in/out with different users (without reboot).

See here: [http://ubuntuforums.org/showthread.php?t=1474985](http://ubuntuforums.org/showthread.php?t=1474985) .

Besides the "killall gnome-panel"-solution, which I also doesn't want to do everytime after boot/login (of course you could write a script for that and include it in the "Startup Applications" via "System -> Preferences"), I would also try another theme, I my issue also with the standard "Ambiance"-theme.

I would suggest a script like this:
```
#!/bin/sh
#wait 5 secs before restarting the panel
sleep 5
killall gnome-panel
```

PS: Please check the next time for any existing threads/solutions, at least at this forum, before opening a new one.;)

---

### Post by foomor on 2010-12-10
Thanks for reply, i will read a given thread :)

> **Krytarik said:**
> PS: Please check the next time for any existing threads/solutions, at least at this forum, before opening a new one.;)
I was searching before i posted, but i had no idea how to name a problem, so probably my keywords were not relevant. Anyway, my bad :-|

---

### Post by Krytarik on 2010-12-10
> **foomor said:**
> Thanks for reply, i will read a given thread :)


I was searching before i posted, but i had no idea how to name a problem, so probably my keywords were not relevant. Anyway, my bad :-|
No big deal, you're welcome!:)

---

