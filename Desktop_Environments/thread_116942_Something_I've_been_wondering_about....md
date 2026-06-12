---
title: "Something I've been wondering about..."
date: 2006-01-13
forum: Desktop Environments
---

### Post by sameat on 2006-01-13
I've been using linux for a while now, and I really love it.  My day job is tech support in an all windows environment, so it's a relief to come home to a machine that just works.

I have a burning question...how do package managers (apt or rpm) apply updates to files that are in use?  Remember, I spend all of my time fixing windows problems.  In the windows world, any serious update requires a reboot.

I love the way you can update your entire linux system and keep working at the same time...I've always wondered how it works.

Thanks to anyone who can solve this mystery for me.

---

### Post by ardchoille on 2006-01-13
From what I have learned, let's look at the following scenario.

You're using myapp-1.3 and you run the update tool. You see an update for myapp-1.3 that updates that app to myapp-1.5. So, you run the update and myapp gets updated. Now, this is why the user should pay attention to what is updated because if you see an update to myapp, you know that you need to exit and re-run that app if you want the new stuff. The thing to remember here is that when you are using myapp-1.3, you are using it in memory (ram) so you can effectively remove the myapp-1.3 executable if you wanted to and still be able to use myapp-1.3 as long as you don't exit the app. When you do exit the app, myapp-1.5 will run the next time you run that app because of the update. The only time you should need a reboot is when you update the kernel and you want to take advantage of new stuff in the new kernel. Anything else can simply be restarted to use the updates.

I haven't used Windows in five years and don't know how that "OS" works, so I can't help you with that.

---

### Post by cwaldbieser on 2006-01-14
[QUOTE=ardchoille]From what I have learned, let's look at the following scenario.

You're using myapp-1.3 and you run the update tool. You see an update for myapp-1.3 that updates that app to myapp-1.5. So, you run the update and myapp gets updated. Now, this is why the user should pay attention to what is updated because if you see an update to myapp, you know that you need to exit and re-run that app if you want the new stuff. The thing to remember here is that when you are using myapp-1.3, you are using it in memory (ram) so you can effectively remove the myapp-1.3 executable if you wanted to and still be able to use myapp-1.3 as long as you don't exit the app. When you do exit the app, myapp-1.5 will run the next time you run that app because of the update. The only time you should need a reboot is when you update the kernel and you want to take advantage of new stuff in the new kernel. Anything else can simply be restarted to use the updates.

I haven't used Windows in five years and don't know how that "OS" works, so I can't help you with that.[/QUOTE]

Windows locks the file when it loads it.  That is why you can't replace it if it is in use.  Lots of installers have code to replace these files right after the system reboots, before the DLL was loaded.

---

### Post by ardchoille on 2006-02-10
That would explain why so many reboots are needed in Windows. Just my opinion, but that is a stupid setup.

---

