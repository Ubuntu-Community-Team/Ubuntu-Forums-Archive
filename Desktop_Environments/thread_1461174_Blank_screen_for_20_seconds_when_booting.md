---
title: "Blank screen for 20 seconds when booting"
date: 2010-04-23
forum: Desktop Environments
---

### Post by Lazze2k5 on 2010-04-23
Hello

I've installed the Lucid Lynx RC, and so far i like it. There's just one issue which is quite annoying. When booting my computer after logging in and hearing the startup sound I get a black screen with just my mouse pointer for about 20 seconds before gnome starts. There's no indication of the computer doing anything, it seems like it's just waiting for something. 

After about 20 seconds gnome starts quickly and runs smoothly. Any ideas what could cause this problem to occur?

Thanks
Lasse

---

### Post by Alan James on 2010-04-23
I have had this same problem with Lucid beta while booting. I figured it was due to the fact that it was beta and not 100% yet. I haven't concerned myself with it yet, but if the problem persists when I install the full release I will come back on here and look for a solution. I recommend that you do the same.

---

### Post by Lazze2k5 on 2010-04-24
Yeah, maybe you're right. But I'm a bit curious to know what would cause it.

I had the same problem a couple of months ago while running Arch Linux when running gnome with compiz. I don't know if it's the same underlying issue but it looks like it could be.

---

### Post by Alan James on 2010-04-24
I am no expert on the complex inner workings of Linux but I would guess the problem would be a video card problem. Again, I have NO real idea. Maybe an expert on here could tell both of us.

---

### Post by Lazze2k5 on 2010-04-25
Yeah maybe, I'm currently running with the proprietary nVidia driver, but the noveau driver gives about the same result.

I would really like to fix this, since it's messing up the otherwise incredibly fast boot time. I barely have time to look at the boot splash when running ubuntu from a ssd.

---

### Post by Lazze2k5 on 2010-04-29
Installed the official release now, but the issue is still there, anyone got any ideas about how to solve it?

---

### Post by talent03 on 2010-04-29
I have had a similar issue with some previous releases. I have not with 9.10. It has been 2 different problems for me before. Once it was trouble with compiz loading on startup. Once it loaded, everything worked great. Another was when I was using preload and that was causing some serious loading lag. 

Different fixes for each. I would think it is a specific package that is causing the problem on your system, based on your configuration. I had other computers that were not affected. It would be best to log this as a bug on Launchpad so people can investigate further; this is to find package or config bug that is causing this.

Even better, explaining your system and any bugs or log files that you encounter that may lead to a fix can definitely help. I will be upgrading today and if I have the problem as well, you better be sure I will be looking for a fix.

---

### Post by Lazze2k5 on 2010-04-29
Thanks, I'll give it a try when I'm getting some free time.

---

### Post by Barafu Albino Cheetah on 2010-05-23
The problem is still there and it is VERY annoying. 
I have the fresh install of release version 32 bit. 
Tried to turn off compiz, avahi, networkmanager and all startup processes. No difference. 
Gnome simply waits for something before loading wallpaper and panels.

---

### Post by texaswriter on 2010-05-23
This thread here addresses this issue

[http://ubuntuforums.org/showthread.php?t=1490249](http://ubuntuforums.org/showthread.php?t=1490249)

HTH

---

