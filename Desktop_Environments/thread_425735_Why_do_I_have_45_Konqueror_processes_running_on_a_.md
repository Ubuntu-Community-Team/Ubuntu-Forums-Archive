---
title: "Why do I have 45 Konqueror processes running on a clean boot?"
date: 2007-04-27
forum: Desktop Environments
---

### Post by monstermunch on 2007-04-27
Hi,

I was looking through my system processes earlier after booting up into my new Feisty Kubuntu installation and found that I had 45 Konqueror processes running! This is from a clean book with a couple of Konqueror windows open and some other apps like kmail and amarok.You can check how many konqueror processes you have going at the command line by typing:

ps -A  | grep konqueror | wc -l

In my Konqueror performance settings, I have both preload boxes ticked and a maximum of 2 instances set to be preloaded. If I reduce the 2 to a zero, a couple of Konqueror processes do disappear.

KDE system guard says that two of my processes were started with "konqueror [kdeinit] --preload" and all the rest with "konqueror [kdeinit] -session ...". 

Am I reading the process list wrong or is there something very odd about this? How many Konqueror instances do you have? Can I fix this?

Thanks.

---

### Post by firephoto on 2007-04-28
It kind of sounds like you have those running and they're getting saved to the session so they restart when you login into kde plus 2 more get preloaded. If that's the case then each reboot should add 2 more konq processes to your count.

---

### Post by miggols99 on 2007-04-28
I think you can fix it by going to K menu >> System Settings >> Advanced tab (or button) >> Session Manager

Then add konqueror to the "Applications to be excluded from sessions" textbox. I haven't tried it out, but it should work.

---

### Post by monstermunch on 2007-04-28
> **firephoto said:**
> It kind of sounds like you have those running and they're getting saved to the session so they restart when you login into kde plus 2 more get preloaded. If that's the case then each reboot should add 2 more konq processes to your count.

Thanks, you helped me fix the problem. After rebooting I still had 45 konqueror processes. You made me think that the extra 43 were caused by some error (or maybe an accumulating error) in KDE, but the session management let them persists. I did a "killall konqueror -9" to get rid of them all and now when I reboot I only have the expected 2. Hopefully it will stay this way; thanks! :-)

---

### Post by monstermunch on 2007-04-28
> **miggols99 said:**
> I think you can fix it by going to K menu >> System Settings >> Advanced tab (or button) >> Session Manager

Then add konqueror to the "Applications to be excluded from sessions" textbox. I haven't tried it out, but it should work.

Thanks. I think this would work but it's useful for konqueror windows to survive reboots.

---

