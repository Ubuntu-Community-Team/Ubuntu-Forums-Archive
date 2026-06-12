---
title: "Custom behaviour for xfce4-power-managee"
date: 2011-11-08
forum: Desktop Environments
---

### Post by exanime on 2011-11-08
Hi all,

So I have this special project I would like to implement but I need some guidance...

I have this little old netbook which I take everywhere... it's running Lubuntu 11.10 which now comes with XFCE4-power-manager.

I use this netbook as my night stand TV and I have a cron job that makes it suspend at 12:30 am with instructions to wake up at 6 am (rtcwake -u -s 19740 -m mem)

What I would like to do is change the default behaviour on xfce4-power-manager so that instead of suspending the netbook (however it normally does) it would run a custom script. The idea is to have it suspend with rtcwake instead of whatever it actually uses to make sure I will get my alert in the morning... 

Any ideas if that is possible?

---

### Post by BobMarleyy on 2011-11-08
This is not an answer to your question, but I got some advice. If you don't mind installing software, try Wakeup.
```
sudo apt-get install wakeup
```
Wakeup allows you to 'wake up' your computer from shutdown. It has some plugins, like a mp3-player.

Sometimes, I run a script when my computer is booted. I do this by creating en event in Orage calendar. You can set a 'procedure' as alarm, where you can enter anything, like run a script. The event can be copied to other days, so it is also easy for everyday use.

Perhaps you find Wakeup useful. And if you also use Orage, you can do what you want. I am no expert, so there might be easier/better solutions.

Cheers,
Bob

---

### Post by exanime on 2011-11-08
Thanks Bob, I will give wakeup a try.

If it works as described it may actually solve my problem because the real issue is that using rtcwake you issue the wake up command as the computer goes into suspend so that timing is critical.

The playing of the music for an alarm is no issue, I have another cron job for that, it starts a particular song I like and raises the volume gradually so I don't get a heart attack! LOL if the netbook is up at the right time the music part is fully taken care off.

I will try wakeup and report my experience

---

### Post by exanime on 2011-11-15
Ok so I gave Wakeup a try and I agree it works well and does everything I needed... thanks Bob!
 
One thing though... when it wakes the computer up it does so 5 minutes BEFORE the indicated time... this is so (I assume) the PC has enough time to fully load before it has to action whatever you set the alarm to do (in my case it plays a song)... on my laptop, if the lid was closed, the laptop did wake up but within the 5 minutes before the actual song played it had enough time to realize it was up and the lid was closed and then it went right back to sleep thus not playing anything...
 
Once I figured this out I stopped being late for work LOL... I disabled the suspend on lid close function and all works just right!

---

