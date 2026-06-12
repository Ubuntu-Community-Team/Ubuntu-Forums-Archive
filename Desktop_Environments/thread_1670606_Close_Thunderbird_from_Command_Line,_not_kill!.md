---
title: "Close Thunderbird from Command Line, not kill!"
date: 2011-01-19
forum: Desktop Environments
---

### Post by lucacerone on 2011-01-19
Hi everybody, someone knows how to close thunderbird from
terminal? 
I don't mean to kill the process,
I just would like a "clean" exit.
I'm asking this because my setup is so that the thrash should be cleared
at exit so and the deleted email are deleted from the
server. I then set a cron task so that thunderbird is killed
but apparently doing so the emails are not deleted from
the thrash (whereas they are if I close the application),
and I'd like to change the task to close thunderbird rather then 
kill the process.

Thanks a lot in advance,
Cheers, -Luca

---

### Post by DougC on 2011-01-19
Try a kill -15 <PID>, this is the nice way and should shut it down nicely as opposed to kill -9 which just terminates the process.

Hope this helps.

This should explain better than I can:

[http://aplawrence.com/SCOFAQ/FAQ_scotec6killminus9.html](http://aplawrence.com/SCOFAQ/FAQ_scotec6killminus9.html)

---

### Post by lucacerone on 2011-01-19
Thanks for your quick answer!
I tried it but it didn't work, though.
Any other suggestion?
Cheers, -Luca

---

### Post by DougC on 2011-01-19
mmm not sure then. Maybe kill -0 <PID>.

---

### Post by lucacerone on 2011-01-19
Sorry but it still doesn't work :)
Thanks again though!

---

### Post by DougC on 2011-01-19
The only other thing I can think of is to use the kill -9 then do something with the trash file (if there is a separate trash file). I don't know if deleting it would work, maybe Thunderbird would just create a new blank file.

I'll stop now as I'm just guessing but maybe it will give you an idea.
(make sure you back everything up if you try any of the above! ;)) 

Sorry I couldn't help more. I haven't used Thunderbird for ages and can't test at the moment.

---

### Post by lucacerone on 2011-01-19
Thanks is any case :)
I've tried -9 as well.. I just think it has nothing
to do with kill though :)
Cheers, -Luca

---

