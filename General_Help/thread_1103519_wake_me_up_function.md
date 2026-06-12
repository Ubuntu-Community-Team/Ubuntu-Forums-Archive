---
title: "wake me up function"
date: 2009-03-22
forum: General Help
---

### Post by sakamoto on 2009-03-22
is there some 'wake me up' function available in ubuntu? i use scheduled tasks in winxp to launch winamp at a specific time for example. thanks!

---

### Post by issih on 2009-03-22
Theres a built in tool called cron, that does these kind of things, but its all command line.

[http://www.manpagez.com/man/8/cron/](http://www.manpagez.com/man/8/cron/)

There is however a little gui front end that you can use called gnome schedule, just grab it from the repositories:

```
sudo apt-get install gnome-schedule
```

Hope that helps

---

### Post by sakamoto on 2009-03-22
thanks. i installed gnome-scheduled. now i want to use rhythmbox to play [http://mp3.streampower.be/radio1-high](http://mp3.streampower.be/radio1-high) each day at a specific time. but im lost with what i have to mention in the command field...

i tried
```
rhythmbox http://mp3.streampower.be/radio1-high
```
but it doesnt work. can you help me further?

---

### Post by issih on 2009-03-22
try something like:

```
rhythmbox-client --play-uri http://mp3.streampower.be/radio1-high
```

I think that should work.

---

