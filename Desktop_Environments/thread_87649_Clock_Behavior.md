---
title: "Clock Behavior"
date: 2005-11-08
forum: Desktop Environments
---

### Post by Ingla on 2005-11-08
Hello.

I'm running Windows on one hard drive and Ubuntu on the other. The locale and time zone are set correctly on both.

But, when I boot into Ubuntu, the clock is two hours ahead of what it says on Windows (which is the correct time). If I synchronize the clock or adjust the time manually*, I find the clock is two hours behind when I go back to Windows.

The OS's seem to be reading the system clock differently. Anybody have any idea what this is about or what to do about it?

*Manual setting of the clock has been a problem. Date/Time GUI asks for a password. I give it and it lets me in. I change what i need to and click OK. Then I get an error notice saying I was logged in as root but something happened and the action wasn't completed. Sometimes it wasn't and sometimes it really was.

Any ideas?

---

### Post by earobinson on 2005-11-08
I searched for "time windows" and i found this: [http://www.ubuntuforums.org/showthread.php?t=71720&highlight=time+windows](http://www.ubuntuforums.org/showthread.php?t=71720&highlight=time+windows)

---

### Post by Ingla on 2005-11-08
Thank you very much.

Unfortunately, the person who answered the post there didn't really know how to fix things.

Also, his answer is a bit confusing. If Windows set the clock to local time, Ubuntu apparently should set it to UTC when I boot in (at least it says it's setting the system clock). If it then "calculates the offset" for display purposes, it should still show the correct time, shouldn't it?

Maybe I didn't understand.

Any ideas?

---

### Post by earobinson on 2005-11-09
as I understand it "right-click clock, preferences, uncheck use utc." is all you must do. did you try this? did it work? what dont you understand?

You can also look at:
[http://www.ubuntuforums.org/showthread.php?t=6285&highlight=time+windows](http://www.ubuntuforums.org/showthread.php?t=6285&highlight=time+windows)
[http://www.ubuntuforums.org/showthread.php?t=17493&highlight=time+windows](http://www.ubuntuforums.org/showthread.php?t=17493&highlight=time+windows)

(I found bot of these using the same search: time windows)

let me know if this helps you at all

---

### Post by Ingla on 2005-11-10
Hi.

Sorry it took so long for me to respond. I'm on the Windows hard disk part of the day (no choice until I find all the programs I need to work on Linux), and can't always jump back and forth to check the clock in the other OS.

Anyway, what I didn't understand was that, if Linux is setting the clock to GMT and then adjusting the display for my time zone, why wasn't it showing the correct time anyway?

Another poster on the thread you showed me said that right-clicking the clock will change the display, but not the UTC setting. So no, I didn't try it.

I followed the advice of another poster (also on the threads you pointed me to), which was to set UTC=no in the startup file.

That did it and both clocks now show the same (correct) time.

Thanks very much. This has been annoying me since I installed Ubuntu.

We're getting there, little by little.

---

### Post by earobinson on 2005-11-11
> Anyway, what I didn't understand was that, if Linux is setting the clock to GMT and then adjusting the display for my time zone, why wasn't it showing the correct time anyway?

Im not sure i understand your Q

---

### Post by Ingla on 2005-11-11
I guess the question is academic now that the clock is working OK.

What I wanted to figure out was that, if Windows sets the clock for local time (in my case GMT+2), and Linux, on boot, changes that to UTC and then adjusts the display by 2 hours to show local time, it should come out OK anyway.

I see Linux "Setting system clock" on boot.

Now that I think about it, the above must be based on a misunderstanding on my part. All this would make sense if neither Ubuntu, nor Windows did anything to the system clock on boot except read it. Changes would only occur if I did something (e.g., I routinely synchronize the clock in Windows manually).

So, if Windows has my clock set to local time (GMT+2), Ubuntu doesn't change that. It just advances the display by two hours ("assuming" it's seeing GMT) and shows me local time + 2. 

Maybe I've got it right this time?

---

### Post by earobinson on 2005-11-11
This sounds like it would worke yes, but I dont know, I have never had this problem, I just searched the forums to try and help you solve it :)

ps could you post your clock settings file for another person that is having this problem.

---

### Post by Ingla on 2005-11-12
Yeah, I know. I just wrote this because you asked what I was in doubt about.

You ***did*** solve the problem.

Thank you very much.

---

### Post by earobinson on 2005-11-14
No problem,

ps if you dont mind could you post your clock settings file for another person that is having this problem.

---

