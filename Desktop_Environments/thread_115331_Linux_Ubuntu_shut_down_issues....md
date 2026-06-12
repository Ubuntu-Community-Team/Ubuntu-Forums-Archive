---
title: "Linux Ubuntu shut down issues..."
date: 2006-01-10
forum: Desktop Environments
---

### Post by Sp@z on 2006-01-10
Ok I have posted something similar before.......this time is is the same issue but a different outcome and this outcome is not something I can live by.......Whether I reboot or shutdown, through a command line or though the KDE (GUI) the system HANGS and won't shut down. THis in itself would be a liveable issue if it would only booted up again without telling me **"Duplicate or bad block"** it will then take about 45 seconds and tell me to run fsck manually, so I do and after going through the list, it tells me to reboot so I do, then it will boot up normally.......Probalem is now that it is having these issues I think in time it will cause issues with my hard drive. 

One of the messages I get says **"/ was not cleanly unmounted"** (isn't this the root?) This has to be a program I installed somewhere because on a fresh install, it will reboot fine. I can see all the processes shutting down, wheras now it is just a blank screen. 

Are there ANY LOGS I can look at to find what exactly is causing the hang on reboot or shutdown? 

Also I am aware that there is another thread on the reboot shutdown issue, but noone mentioned the fsck failing and such, control d will reboot the system but only to make me go through the whole manually running fsck again. 

I love linux and KDE, but if I can't resolve the issue without reformatting I have to go back to windows till the issue is resolved, I REALLY don't want to do that.

Someone mentioned in another post that downloading some bits of Dapper Drake will help the issue but they posted no info on how to do that, and I am not sure how legit that is since Dapper isn't even ready....Thanks for the help gang.........if I ever resolve these issues I can learn more about Linux and start returning the favors by posting more to help others..........

---

### Post by Sp@z on 2006-01-11
it is all video card related.........kinda got it fixed

---

### Post by Olflo on 2006-01-11
Well, nice it seems to have worked out for you, but I do think this problem is serious since I'm having the same thing.
There are various ways my system hangs but one of them is very much like what you decribe. I also posted this on another thread and i want to restate it here.
another thing that happens frequently is that on shutdown the screen gets written full of cryptic things, hex code and so on until a certain point when the system hangs and wont shutdown.
The following boot sometimes is straightforward, sometimes it also tells me to fsck because "/ was not cleanly unmounted".
All this was in Hoary and was my primary reason to make a clean install with Breezy, which went fine and is running to my satisfaction, just like Hoary was before, until the day when I did something, dont know what.
I kept the faulty installation of Hoary, installed Breezy to another hdd and I would love to let someone from the devel team look at any of my logs, maybe it'd help resolve this problem in the future. You can have it all, just let me know.
hope someone reads this who can make something from it.

---

### Post by Sp@z on 2006-01-11
YOur experiancing the same things I did as well. I am POSITIVE that there is more than it being a video driver issue though. Also in another thread the Dapper Drake Team is aware of the issue and trying to resolve it before the relaese of Dapper. I am not sure if they have narrowed it down to the video or where they stand on it, but they are aware of it. Good luck to you and if per chance your running Nvidia drivers the HOW TO has been updated and I had a few issues (User error, not breezy) but it is resolved now. Good luck to you and if I get more info I will pass it along to you.

---

### Post by Brigrat on 2006-01-22
Hey,  I am having kinda the same issue.  I upgraded the 386 to the 686 kernals and my box hangs on shut down.  I followd some fix suggestions and it would just reboot.  No shut down errors just hang up on the shutdown and after I manually shut it down it would reboot.  Please see my post in the bug report section.  HELP!

---

