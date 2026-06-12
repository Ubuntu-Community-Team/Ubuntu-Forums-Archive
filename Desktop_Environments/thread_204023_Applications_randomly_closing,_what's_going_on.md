---
title: "Applications randomly closing, what's going on?"
date: 2006-06-26
forum: Desktop Environments
---

### Post by Biffy on 2006-06-26
This is a long story but i'm gonna try to make it as short as possible:

When i was using Breezy, i had some problems with applicatons randomly shuting down. The application will just dissappear without any warnings. I had problems with my webbrowsers. Firefox, mozilla and Opera. They would just shut down randomly and it usually happened when clicking on a link. I also had problems with LICQ, just shutting down. Licq did only crash when i was NOT using the computer, wich is weird.

Anyway, i found no solution to this problem, so i tried upgrading to Dapper unstable. I think it was flight 6 i first upgraded to. This solved the problem! Running Dapper unstable solved the problem and Licq didn't crash one single time and my browsers worked fine too. Sure, firefox crashed one time but Epiphany worked just great.

So, i was happy running flight 6 and everything worked fine. Then, the stable version of Dapper was released and i upgraded. Now, theese problems are coming back! Epiphany has crashed when not even being at the computer (don't know if it's related to my problems, might just be an innocent crash) and LICQ has started to crash again.

So i tought i needed a reinstall but then i searched the forums and i see that i'm not the only one with this problem. Firefox seems to be the application that most people have problems with, but i also found a couple of threads describing people with random applications that would just crash.

I found this post very interesting:

> i came here b/c i've beeen experiencing MANY MANY crashes after Dapper final I never had dating all the way back to Flight 5. <-- Written by magomago. See the thread here:

[http://ubuntuforums.org/showthread.php?t=187263&page=2&highlight=1.5.0.3](http://ubuntuforums.org/showthread.php?t=187263&page=2&highlight=1.5.0.3)

And he is confirming what i'm saying. Both of us never had any problems with applications shutting down back in Dapper unstable, but in the stable version we got 'em. I updated my unstable Dapper 28 may and my system was fine. A couple of days later when upgrading to the stable version, things went unstable. And there couldn't have been too many updates in thoose days?

**This is a major problem!** How can this be fixed? Why is the unstable version working fine when the stable isn't? Any ideas?

Im running kernel 2.6.15-25-686 . Could this be related to the kernel? Sorry for my bad english btw.

---

### Post by Biffy on 2006-06-27
No solution to this whatsoever? I'm getting worried that this is unknown to the Ubuntu devs.

---

### Post by PriceChild on 2006-06-27
It seems like its only you two :S

Maybe you could compare hardware with that other guy.

Try doing a memory test.

Is this occuring on a completely fresh install? You haven't tinkered a bit too much?

---

### Post by bruce89 on 2006-06-27
Try running the applications from the command line and post any output.

---

### Post by edopizza on 2006-06-27
I have the same problem but with a shorter story. Firefox worked fine on Breezy (just like all the rest) but after the major update to Dapper (and also I think of firefox itself) it crashes let's say once a day. My last crash happened during the saving of a single page OO write document.

---

### Post by Biffy on 2006-06-27
[QUOTE=bruce89]Try running the applications from the command line and post any output.[/QUOTE]

They are segfaulting. You can read some of my other posts (written a while ago) about this problem:

[http://www.ubuntuforums.org/showthread.php?t=161116](http://www.ubuntuforums.org/showthread.php?t=161116) 

[http://www.ubuntuforums.org/showthread.php?t=155167](http://www.ubuntuforums.org/showthread.php?t=155167)

edopizza: I knew i wasn't alone. :)

Pricechild: No, i've had this installation since warty. Yes, it's been here a while. I've also felt that a reinstall would be nice, but at the same time, that is stuff i wanted to get away from. You know, the Windows "use your computer in one year then reinstall so all your stuff is gone" -kinda thinking.

Actually, Opera crashed A LOT when having this problem but the new version (Opera 9) has been running great since friday. Back then, Opera crashed at least once in a couple of days.

---

### Post by AlokR on 2006-06-28
Ah, glad to have found this thread, but not glad that we are having this issue...I had never experienced such crashes earlier, but since I upgraded to Dapper:

Multiple applications, including Firefox, Thunderbird, Mozilla Composer, OpenOffice have randomly/repeatedly crashed/disappeared/closed without warning and without leaving any trace/core file - any pending saves are all lost each time.

The closest pattern that I can detect is that I was doing some type of mouse click/activity at the time (I think this is consistent, but cannot be 100% sure) - I know that twice in Thunderbird, I was scrolling when the application/window simply vanished.

My system is:

# uname -a
Linux ubuntu 2.6.15-25-386 #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006 i686 GNU/Linux
# Fujitsu C (C2340) Series Lifebook (no mods)
# Internal mouse pad disabled (modprobe -r psmouse) with an external USB Logitech mouse
# Fresh installation of an older rev of Ubuntu, then incremental upgrade to the latest release
# Exlusively running Ubuntu, no dual partition/no windows

Quite unreliable for any serious work, since I have lost quite a bit of it.

Will anxiously watch this thread/await suggestions - thanks much!

Alok

---

### Post by Biffy on 2006-07-01
Knew i wasn't alone with this. Im just having LICQ crashing (has not happened in a while toug) so i guess im kinda lucky. 

What should we do about this? We need to get in contact with the Ubuntu team and ask them about this.

---

### Post by Biffy on 2006-07-03
Bump!

---

### Post by fonzai on 2006-07-07
I'm experiencing the same problem i.e. my firefox and thunderbird are crashing constantly (maybe once in an hour) ](*,) . I'm running dapper (-k7) with all latest upgrades. I never had this problem before, but now it has been bugging me for a few weeks.

Ideas, anyone? :-k

---

### Post by Biffy on 2006-08-08
Upgraded to Opera 9.01 the other day, and Opera blinked out on me again. Has not happen once since 9.0 beta. 9.01 has crashed once in a week, and im gonna give it another chance. I have removed the package from my system and installed it from scratch.

If this happens again i need to go back to 9.0.

---

