---
title: "Huge fonts at login window &amp; title bars..."
date: 2007-11-18
forum: Dell  Ubuntu Support
---

### Post by cyberick on 2007-11-18
Hey guys, I installed Ubuntu 7.10 on my Dell Inspiron 6000 today, but I'm having problems with either the fonts' sizes or graphics configuration.

I had Ubuntu 7.04 and everything was fine, then I decided to clean my HD completely and install 7.10 (instead of upgrading) but I noticed there was something wrong at the GUI installer... the title bars' fonts were HUGE! 

After disabling desktop effects and enabling them again, the title bar's fonts were back to normal, but I still having those huge fonts at the login window.

Anyway... here's a screenshot of the title bars...

PD: I don't know why, but I got the same problem at the GUI installer of Backtrack2... 


Thanks in advance;
-Cyberick

---

### Post by bluedragon436 on 2007-11-18
I had a similar issue on my laptop when I installed 7.10, but now while I had 7.04 installed....I am not sure if this will work for yours, but since I didn't care what it did as long as it was fine once it was all started up, I just carried on and installed the restricted drivers for my video card, and did the updates, then restarted and everything was fine again, like I said don't know for sure this will work in your situation, but it did for mine, thank goodness...

---

### Post by cyberick on 2007-11-21
> carried on and installed the restricted drivers for my video card, and did the updates, then restarted and everything was fine again, like I said don't know for sure this will work in your situation, but it did for mine, thank goodness...

That didn't work for me. I consulted my problem on the Ubuntu IRC channels and someone told me it was most likely that my video card was not well configured. However, it's neither my Intel video accelerator nor login resolution since the login window looks just perfect. The only problem is the font's size at the login box. 

I already tried modifying my gdm.conf following the instructions in this post:[http://ubuntuforums.org/showthread.php?p=3609621]("http://ubuntuforums.org/showthread.php?p=3609621"). Still no results. :\

I know there're a few people who have/had this issue. If you found a way to fix it, please give me a hand! I can't even sleep... 

Again, thanks for your help;
-Cyberick

---

### Post by cyberick on 2007-11-21
Woot! It's fixed... I just missconfigured (intentionally) the screen resolution by setting it up to 600x800... 

After rebooting, the system recognized the low graphics' problem and prompted me to fix it by manually selecting my screen resolution... and voilà! my screen resolution (1280x800) was recognized... Now the fonts at the login window are fine.

Best regards,
-Cyberick

---

### Post by southernpsy on 2007-12-08
I am a first time linux user.  I installed Gutsy on an external HD about one month ago.  I had the same problem listed here also with a Dell Inspiron 6000.  I got it to recognize my screen resolution and everything look fine now after logging in.  However, the login screen still has huge font.  Any thoughts?

---

### Post by jpoRS on 2008-04-03
Cyberick, what exactly did you do.  I am having the same problem.

Strangely enough I also have a 1280x800 monitor (hp), could it be our "unusual" screen resolution that is at fault?

thanks
jim

---

