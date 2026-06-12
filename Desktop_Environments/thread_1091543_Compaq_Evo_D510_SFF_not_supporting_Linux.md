---
title: "Compaq Evo D510 SFF not supporting Linux"
date: 2009-03-09
forum: Desktop Environments
---

### Post by mubashar on 2009-03-09
Hi All,
I am trying to run Ubuntu 8.10 and kubuntu 8.10 on the machine Compaq Evo D510 SFF having 2.4 GHz CPU, 512 MB DDR Ram, 40 GB H.D.D.
Installation gets complete successfully, but in case of Kubuntu after logging in, system gets halt. and same in case of ubuntu.
Please tell me some solution to this.
Thanks
Regards
Mubashar Ahmad

---

### Post by KaMii on 2009-03-09
hi,

i have exactly same model. And mine is running perfectly. i am running ubuntu interpid(8.10)... haven't tried kubuntu yet...

i have the same processor with ram upgraded to 1 gb and graphics card fitted in the agp slot(Nvidia Geforce fx5200)...

if you please briefly describe your problem... i may be able to help you then...

thanks

---

### Post by mubashar on 2009-03-10
Thanks for your reply.

Both ubuntu and kubuntu get halt my system.

In case of kubuntu, after logging when welcome sound starts, then the system gets halt.

And in case of ubuntu, after logging I only see a black screen nothing more.

I tried it on 1000 MHZ system with 256 MB ram, there it runs perfectly. but i dont know what is problem in my system.

Looking for kind response.

Thanks

---

### Post by KaMii on 2009-03-10
looks like there's some kind of problem with your graphic card or its drivers... are you using built-in intel graphic adapter?

I will remove my AGP graphic card and will try ubuntu with my built-in to see what happens because both of ours is same...

---

### Post by ddvanrooy on 2009-03-21
> **mubashar said:**
> Hi All,
I am trying to run Ubuntu 8.10 and kubuntu 8.10 on the machine Compaq Evo D510 SFF having 2.4 GHz CPU, 512 MB DDR Ram, 40 GB H.D.D.
Installation gets complete successfully, but in case of Kubuntu after logging in, system gets halt. and same in case of ubuntu.
Please tell me some solution to this.
Thanks
Regards
Mubashar Ahmad

Hi
I have same problem. I posted on the forums a weeks ago about it. I m bit of newbie with Ubuntu.Anyway I finally managed to get it working using a pacakage "Super Ubuntu". Why this package worked and 8.10 didnt, I have no idea, since they are suppose to be same kernel etc. I also tried 8.04 (which runs perfectly on my Thinkpad) and same problem on the EVO

If you manage to get it working with "normal" Ubuntu I'd like to know, because I had several other problems with this Super Ubuntu. 

DD

---

### Post by ddvanrooy on 2009-03-21
Hi 

I just found in this forum from last year: It is same problem also on EVO. At the end of the post they claim they tried it and it works although I havent tried myself - cant wait !!! I'm really curious to hear if you get this going, since I dont have physical access to my EVO's right now.....

Good luck
DD 



(all credits to the authors)
(I dunno howto link different threads)
------------------------------------------------------------------
[SOLVED] 8.10 Intrepid hangs at startup

That is, now it runs fine. From August 13 until today, booting up would give a "black screen of death" when the desktop should have loaded.

So I would install (doesn't use compiz)
Boot in rescue mode (doesn't use compiz)
At the selection menu
root shell prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume normal boot.

So the "official fix" came in. See Launchpad Bug #259385. With compiz version 1:0.7.8-0ubuntu4.1 it simply "blacklists" a number of Intel video chips including mine and then compiz won't be run. Now it should have just dropped back to the 8.04 level of compiz which ran, however it did use up CPU cycles and on this older computer I'd select Visual Effects None.

The "official fix" is just like removing compiz except of course compiz code still takes up hard drive space, just never executed.
--------------------------------------------------------------------

---

