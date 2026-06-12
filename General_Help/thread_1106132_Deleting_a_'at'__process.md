---
title: "Deleting a 'at'  process"
date: 2009-03-25
forum: General Help
---

### Post by 7raTEYdCql on 2009-03-25
I am in a bit of a fix here

I have created an alarm which plays in the morning. Just so that i can test it i tried it in the night before going to sleep.

I ran the at command, and looped the mplayer to play my alarm bell 1000 times. Juat for the sake of it. Now i dont know how to stop it.

```

at 22:02
>>mplayer --loop 1000 'Alarm.wav'
...

```

I tried the atrm command. The process got deleted but the alarm is still going on. Can someone help, i want to catch on some sleep.:)

---

### Post by Anthon on 2009-03-25
killall mplayer

---

### Post by 7raTEYdCql on 2009-03-25
Thanks that was a relief.

---

