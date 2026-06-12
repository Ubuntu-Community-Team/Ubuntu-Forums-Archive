---
title: "Unity doesn't want to appear..."
date: 2012-06-06
forum: Desktop Environments
---

### Post by L R C on 2012-06-06
First of all, I think this is the right subforum, if it isn't then I'm sorry.

I recently backed up my data and did a fresh install of Ubuntu 12.04 (x64) over 11.10. I restored it from the backup, which seems to have worked, and I enabled proprietary drivers for my graphics card. Now unity doesn't seem to work at all - I don't have the side panel or the panel at the top which has all the useful stuff on it. If all windows are minimised, I can only see the background, and the only way to launch programs is to use Ctrl+Alt+T to open the terminal and then type in the command, for example "firefox". Can anybody help me out? I want to get my computer back to how it was before as quickly as I can.

---

### Post by blackbird34 on 2012-06-06
have you tried : 

```
unity --reset
```


to restart  Unity?

---

### Post by L R C on 2012-06-06
I have, it did very little apart from removing the window title bars. The 2D version of Unity is fine, by the way.

---

### Post by wilee-nilee on 2012-06-06
> **L R C said:**
> First of all, I think this is the right subforum, if it isn't then I'm sorry.

I recently backed up my data and did a** fresh install of Ubuntu 12.04 (x64) over 11.10. I restored it from the backup**, which seems to have worked, and I enabled **proprietary drivers** for my graphics card. Now unity doesn't seem to work at all - I don't have the side panel or the panel at the top which has all the useful stuff on it. If all windows are minimised, I can only see the background, and the only way to launch programs is to use Ctrl+Alt+T to open the terminal and then type in the command, for example "firefox". Can anybody help me out? I want to get my computer back to how it was before as quickly as I can.

What is your definition of proprietary drivers, is this from the repos or 3rd party?

Did you remove any in place drivers before adding the ones you did?

Was this a backup from this computer?

The first bold section needs to be clarified within its meaning in relation to the above questions.

---

### Post by Viper1987 on 2012-06-06
Try installing the GPU driver from the official site (if available). Worked for me!

---

### Post by L R C on 2012-06-06
> **wilee-nilee said:**
> What is your definition of proprietary drivers, is this from the repos or 3rd party?

Did you remove any in place drivers before adding the ones you did?

Was this a backup from this computer?

The first bold section needs to be clarified within its meaning in relation to the above questions.

I used the driver that the additional driver utility found for me, I didn't go out and look for drivers.

It was a fresh install so there weren't any drivers in place

It was a backup from this computer, not of the whole system but of the home folder - I probably shouldn't have mentioned it since it doesn't really affect the system.

---

### Post by wilee-nilee on 2012-06-06
> **Viper1987 said:**
> Try installing the GPU driver from the official site (if available). Worked for me!

Bad advice, period, don't just spit out what you think will work.

May have worked for you but you will have problems, and the last ditch way to fix this sort of problem.

---

### Post by deadflowr on 2012-06-06
> **wilee-nilee said:**
> Bad advice, period, don't just spit out what you think will work.

May have worked for you but you will have problems, and the last ditch way to fix this sort of problem.

Agreed. Installing the drivers outside the Ubuntu channels will make it so you'll have to install any driver updates yourself, in the long term. Which would mean keeping up with any new news on your card.

From what the OP posted, Unity is not broken, compiz is. I would suspect that you are using a Nvidia card. There are bug reports for this issue. If you log out and in the selection icon next to your name, select unity2d and a basic unity2d setup will run.
It's a quick fix and hopefully will your problems with your graphics card will be resolved soon.

---

### Post by L R C on 2012-06-06
> **deadflowr said:**
> Agreed. Installing the drivers outside the Ubuntu channels will make it so you'll have to install any driver updates yourself, in the long term. Which would mean keeping up with any new news on your card.

From what the OP posted, Unity is not broken, compiz is. I would suspect that you are using a Nvidia card. There are bug reports for this issue. If you log out and in the selection icon next to your name, select unity2d and a basic unity2d setup will run.
It's a quick fix and hopefully will your problems with your graphics card will be resolved soon.

So there's nothing I can do about it? Will reverting to Ubuntu 11.10 fix this problem?

Thanks a lot for your help, by the way, everyone.

---

### Post by NikTh on 2012-06-06
Hi , 
try to create a new user and login , if you see that Unity works with new user then you have 2 options

1) Give this new user admin privileges and move your files (after that , delete old user)

2) login from old user and try to delete the .compiz (hidden folder) which is in your home folder. But its hidden , to see it press Ctrl+H
Thanks

---

### Post by deadflowr on 2012-06-06
> **L R C said:**
> So there's nothing I can do about it? Will reverting to Ubuntu 11.10 fix this problem?

Thanks a lot for your help, by the way, everyone.

Well there is always something to try. Even though I personally recommend against it, for my above post mentionings, you CAN try and install the drivers from the graphics card site, make sure to follow any directions.

But first, and probably something that seems lost throughout this thread. What is your graphics card?

To find out:

```
lspci | grep VGA
```

From there we can get a sense of what you might be able to do.

---

### Post by L R C on 2012-06-06
> **deadflowr said:**
> Well there is always something to try. Even though I personally recommend against it, for my above post mentionings, you CAN try and install the drivers from the graphics card site, make sure to follow any directions.

But first, and probably something that seems lost throughout this thread. What is your graphics card?

To find out:

```
lspci | grep VGA
```

From there we can get a sense of what you might be able to do.

It's a Nvidia 9400 GT, I think it's the older version with 512mb of RAM or whatever it's called on graphics cards...

---

### Post by L R C on 2012-06-07
**To anyone else who is having this problem:**

I decided to reinstall 11.10 but ended up with the same problem. I installed the CompizConfig settings manager thing (using the 2d environment, you could do it via a terminal as well) to check if I could use that to fix it. When I opened it up it was obvious what was wrong: the "Ubuntu unity plugin" was disabled. Enabling it fixed everything...

I feel incredibly stupid for not thinking of this earlier, but 12.04 was annoying me anyway, so yeah...

---

