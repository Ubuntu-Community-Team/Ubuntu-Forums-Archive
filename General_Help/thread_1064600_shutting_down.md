---
title: "shutting down"
date: 2009-02-09
forum: General Help
---

### Post by tompask on 2009-02-09
Hi i am experiencing a weird problem when i go to shut down the screen goes off but my computer stays on i cant do anything with it as there is nothing on the screen but the computer does not switch off on my windows partition i have no problems shutting down!

any ideas?:)

---

### Post by sleepyjon on 2009-02-09
How do you try to shut it down?

What's the exact error message?

---

### Post by tompask on 2009-02-09
That's the thing there is no error message!
I just go to the right top hand corner go to shut down screen switches off
tower stays on and don't get any life from the screen then! its a weird one I know!  :s

---

### Post by Peter09 on 2009-02-09
There is a shut down bug drifting around, however a few things to try.

Try using the shutdown command - 

```
sudo shutdown -h now
```

it may give you a clue as to what is holding the machine.

Also try using the shutdown icon which appears when you click the System menu. It looks the same as the other but I've noticed you can sometimes get different results.

---

### Post by tompask on 2009-02-09
thanks for that he command line works just fine!
Any ideas on how to rectify the problem? 
Shutdown that way all the time will get annoying after a while 
Appreciate the help

---

### Post by thestig_992 on 2009-02-09
as a quick fix you could make a launcher that exectes that command

since you need to be root i think it will ask you for your password though, which will get just as annoying

further than that i really dont know

---

### Post by Peter09 on 2009-02-09
Here is one of the bugs around this area

[https://bugs.launchpad.net/ubuntu/+bug/193125](https://bugs.launchpad.net/ubuntu/+bug/193125)

---

