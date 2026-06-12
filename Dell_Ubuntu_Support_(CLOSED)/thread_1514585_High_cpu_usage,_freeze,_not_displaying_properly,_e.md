---
title: "High cpu usage, freeze, not displaying properly, etc"
date: 2010-06-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by RainingMan on 2010-06-21
Hello,

Skip to the symptoms part if you don't feel like reading my story. I feel like writing a lot in order to pinpoint the problem.

[Hardware/software part]
I have a DELL dimension 520
Processor : intel core2duo 6300 1.86GHz
Memory : Originally 1 go which I added 2 go for a total of 3 go.
Video card : Nvidia geforce 8600.
Hard Drive : 280go sata - 500go sata 

Dual boot with grub2 - Ubuntu 10.04 64 bits and Windows Seven 64 bits


[My computer problems story]
{Chapter 1 : windows seven]
A while ago, I've gone to a lan, desactivating my windows seven firewall but not my avg anti-virus.
It may not be the cause, but it's the beginning. There, avg detected a virus on my friends computer resulting in me not downloading the file. In the following days, my windows seven (ubuntu part soon, don't worry) began to freeze/lag/etc and I attempted a recovery from before the lan. My recovery lasted forever and, 2-3 hours later, I decided to restart my computer (while recovering) because it was so damn long (normally, it takes about 30 minutes I think...not certain thought). Surprise, I couldn't load seven at all. Next thing I've done is to attempt an automatic repair from seven's boot. Lasted long enough for me to understand it will never...never finish. I decided to reinstall seven -> same thing, then reformat and reinstall and it worked!...until I updated it and it froze in the process -> me restarting the computer -> couldn't load seven. There, I decided to do the same exact thing but my computer froze in the process of displaying the menu of installation. From this point, I changed my opinion of "omg this virus is so badass" to "omg, it may be my hardware". 

[Chapter 2 : Ubuntu]
Having Ubuntu in dual boot, I finally decided to completely erase windows seven and continue my trip with Ubuntu (I was so tired of my windows trip). I was calmly surfing when Ubuntu froze for a couple of second. I was "no...no...impossible" and I kept surfing. Some time later, between two freezing (they don't occur THAT often, maybe 1 time every hour when I'm only on the internet), my computer restarted for no reason. Since then, I'm monitoring it while searching for possible solution. In the process of recovering grub2 memory test from the /etc/default/grub in order to check if it's my memory, I've found something interesting.

Wow...actually, I was planning on giving you screenshots of my system monitor but I can't, for reason I'll write down in a minute.
So here I am, with absolutely nothing working (ubuntu works fine with firefox open and no lag nor anything).

[Problems part]
1. Windows froze several time and couldn't boot because of it.
2. Ubuntu froze much less then windows and for 5 seconds maximum. When it freeze, the cpu usage go to nearly 0% until unfreeze.
3. Ubuntu restarted once, for no reason.
4. /tmp directory was not there (I didn't deleted it) so when I restarted, ubuntu created it.
5. When I open gnome terminal/gedit/about 50% of programs under linux, the windows open, but only the border with a big ubuntu theme color where text or anything else is supposed to be. I know the controls inside the window works, I clicked on cancel in a certain window where it was all brownish/gray ubuntu theme color and it worked (no button were present). 
6. When I open those same programs, one of my processor rise at 100% while the other continue doing nothing, which I think is normal...until I open more than one problem program, where all my processors are used at 100% without any lagging or anything. Even a screenshot rise my cpu to 100%.

[My guess]
1. Something to do with a bad memory, I'll run a memory test and post/edit if the memory is the cause.
2. My processor since he rise to 100% and lower to 0% in particular occasion.
3. Virus (which I doubt would affect linux)

I think my hard drives are okay, but I'll test them out too.
I will upload picture if I can.
There may be more than one problem.

Thank you.

---

### Post by RainingMan on 2010-06-21
Hello again,

After some tests with dell utility partition, it seems like my hard drive is failing me.
I am sorry for the useless thread since I should have done the test sooner.

So everything is solved.

Raining man.

---

