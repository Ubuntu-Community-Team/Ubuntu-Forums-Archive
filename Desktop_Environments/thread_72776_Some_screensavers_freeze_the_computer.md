---
title: "Some screensavers freeze the computer"
date: 2005-10-07
forum: Desktop Environments
---

### Post by PatrickMay16 on 2005-10-07
Hello, 

Some of the screensavers available through System -> Preferences -> Screensaver freeze the computer, and the only way to get out of it is to reboot. When this happens you can still move the mouse, but the image the screensaver produced doesn't move any more, and nothing you can do will help you out of it.

Has anyone else had this problem?

---

### Post by frodon on 2005-10-07
Yep for me this problem is due to xcompmgr, so I don't use a screensaver but just a black screen and it solve the problem.

---

### Post by mcduck on 2005-10-07
Have you installed drivers for your graphics card? Some of those screensavers use OpenGL..

---

### Post by PatrickMay16 on 2006-04-29
I discovered what the problem was. It wasn't just the screensavers; it was anything using direct rendering, like the 3D screensavers, Mupen64, etc; the screen would always freeze when using direct rendering. Strangely, I could still move the mouse pointer around, but nothing else would work. 
It seems like a problem specific to the free ATI driver.

I fixed this problem, and now I have the solution for you all.
Using the free ATI driver, I am experiencing a rich gaming experience. 

The solution was to enter the BIOS and disable AGP fast write, then to set the AGP 2.0 mode to 4x. In my case, it was already set to an option called "4x/auto", so I just left it like that. 

Then I added this to the "Device" section of the /etc/X11/xorg.conf file:
```

Option "AGPMode" "4"

```

And then I went and played MARIO 64!!!!!1 for several hours using Mupen64 0.5 , and it worked fine!!! Then I went and stared at the "endgame" screensaver for several minutes, and it also worked fine. 

My video card is an ATI Radeon 9000Pro. I hope this helps other users of the same/similar cards. Let me know if it helps you at all.
I don't fully understand why this solution works, but it does. I came on it by accident. Maybe if some more technical people read this thread, they could explain it to me? I would appreciate it.

---

### Post by Nu-Buntu on 2006-05-02
Patrick,

Thanks for the solution. I have been on Breezy since it came out, and Hoary before that. I got brave last weekend and finally did a dist-upgrade to Dapper, but X wouldn't start. So I did a full install of Dapper, and it was fine, except the screensaver locking the system as you described. SO...I did an install of Fedora Core 5, which I am running at the moment. I still like Ubuntu better, so once we get final code on Dapper, I will be back. Therefore, I am saving your solution.

---

### Post by Tristan9669 on 2006-05-24
[QUOTE=PatrickMay16]I discovered what the problem was. It wasn't just the screensavers; it was anything using direct rendering, like the 3D screensavers, Mupen64, etc; the screen would always freeze when using direct rendering. Strangely, I could still move the mouse pointer around, but nothing else would work. 
It seems like a problem specific to the free ATI driver.

I fixed this problem, and now I have the solution for you all.
Using the free ATI driver, I am experiencing a rich gaming experience. 

The solution was to enter the BIOS and disable AGP fast write, then to set the AGP 2.0 mode to 4x. In my case, it was already set to an option called "4x/auto", so I just left it like that. 

Then I added this to the "Device" section of the /etc/X11/xorg.conf file:
```

Option "AGPMode" "4"

```

And then I went and played MARIO 64!!!!!1 for several hours using Mupen64 0.5 , and it worked fine!!! Then I went and stared at the "endgame" screensaver for several minutes, and it also worked fine. 

My video card is an ATI Radeon 9000Pro. I hope this helps other users of the same/similar cards. Let me know if it helps you at all.
I don't fully understand why this solution works, but it does. I came on it by accident. Maybe if some more technical people read this thread, they could explain it to me? I would appreciate it.[/QUOTE]
thank you so much, it worked

---

### Post by RudolfMDLT on 2006-08-09
Thanks man! That really makes life better!

---

### Post by axle_foley00 on 2006-08-26
I am having a similar problem and am considering using the solution however I wanted to know if this affects the performance of the AGP card on Windows? Just curious since I play games in Windows and not under linux.

---

### Post by Tristan9669 on 2006-08-26
I dont think it would.

---

### Post by axle_foley00 on 2006-08-27
> **Tristan9669 said:**
> I dont think it would.

Ok cool. Thanks.

---

### Post by aleska on 2006-08-27
I just set up Xubuntu on an old P2 machine that happens to have an ATI Radeon All-In-Wonder 9000 video card.  Anyway, was running into this exact problem.  I will try the fix as soon as automatix is done pimping my ride (can't believe how long it takes to install stuff with these older pcs).  
Curious, have you ever been able to figure out how to get the video capture working on this card?  (I thought you mentioned having the same card).  Would love to know.
Thanks!
-aleska

---

### Post by aleska on 2006-08-28
Well I went into my BIOS settings and didn't see anything remotely like AGP fast write or any other settings referred to in this how to.  Could that be b/c this is such an old pc?  
Anyway, I thought that maybe, I AGP fast write was something new systems had and that I could just pick up the howto with the edit of xorg.conf.  Made the change.  Rebooted.  Went straight to check my screensaver stuff, and...same problem.  I had to restart my pc.
Should I be trying the newer ATI driver?

---

### Post by kharl on 2007-01-14
Thanks a lot! It solved the problem on my 6.06.1 installation.

---

