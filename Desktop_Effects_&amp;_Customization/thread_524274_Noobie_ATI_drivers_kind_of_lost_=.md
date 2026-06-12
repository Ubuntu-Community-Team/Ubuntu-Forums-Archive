---
title: "Noobie ATI drivers kind of lost =/"
date: 2007-08-12
forum: Desktop Effects &amp; Customization
---

### Post by VAsHachiRoku on 2007-08-12
Ok been a windows user for ever and figured time to switch to linux OS.

I have spent most of the day trying to figure out this ATI drive mess, I almost bought an NVIDIA card because I'm getting so ticked.

Ok a couple of things I'm stuck on even though Ive read just about every thread and google link I could find and have messed it up a couple of times and reloaded.

I have a ATI 9800XT pro.
I installed CompizConfig
I installed ATI Drivers from ATI side
I enabled the restricted ATI driver - the control center works.
fglrxinfo >>
> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 XT
OpenGL version string: 2.0.6334 (8.34.8)


This is what I would like and I would be happy, 1280x1024, and I would like the cube to work.
After I installed then ATI drivers the DESKTOP EFFECTS doesnt work anymore.

When I first installed Ubuntu 7.04 and did all the updates that menu was there, the cube worked but my windows were screwed up (no close, minimize, couldnt type in windows etc), but it did work.

After the ATI drivers and the Compiz - enabling the cube nothing. I guess there is something I'm missing. Also I am still new but not afraid of command line at all. I just really wish I could get my 1280x1024 and the cube would be nice.

Any suggestion? I tried to edit all the files I found online, and I'm really not sure going on 5 hours and have drank way to much while trying all this.

Thanks for the help

---

### Post by dmacdonald111 on 2007-08-13
I know exactly how you feel. I had the same problem when I last installed linux (a year ago) but I have recently installed Feisty (last night) and setting up an ATI card is a lot easier now. You should be able to go to System, Administration, Restricted Drivers and then turn on the ATI accelerated graphics driver.

That&#347; all I found that I had to do. If you have any further probs., you could try;

[http://ubuntuforums.org/showthread.php?t=515573&highlight=install+ATI+feisty](http://ubuntuforums.org/showthread.php?t=515573&highlight=install+ATI+feisty)

Hope you get it working okay!

---

### Post by conradlyn on 2007-08-13
this reply is based on my memory,wish it didn't have many mistakes.i only want to halp.:)

maybe you should disable that restricted driver,at least i did this and the effect went back.

then,the window manager problem also came to me too after i first time installed compiz fusion.to solve this problem,you need to let the emerald window manager on the go.

they say,you add "compiz--replace" and "emerald--replace" to the session can work,but this method didn't do any good to my system.and to avoid this command line operating,you should get a simple and gui style manager,that would be the "fusion-icon".

to install fusion-icon,simply type "sudo apt-get install fusion-icon" in the terminal,after it is installed,open the session window and add "fusion-icon" to it,then restart your computer.

there still is work to do after your pc restarted,to get your window control buttons back,you should install a emerald theme,which can be downloaded anywhere,also, you should change the window manager to emerald and it should work after all these have been done.

again,wish it helps.:)

---

### Post by miggols99 on 2007-08-13
The restricted ATI drivers do not support AIGLX. This means that if you want desktop effects, you'll going to have to install XGL. A search around the howtos forum will give you a nice tutorial for you to follow.

---

### Post by kellemes on 2007-08-13
Correct.
I have my x1650 pro running with XGL and enjoy all the funstuff this card has to offer.
Please don't ask me how I did it, it's brings back memories that kept me awake for a long time. #-o

---

### Post by VAsHachiRoku on 2007-08-13
[http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)

That fixed my issue after removing compiz, then installing GXL.

I just need to get 1280x1024 and start learning what the different features are.

---

