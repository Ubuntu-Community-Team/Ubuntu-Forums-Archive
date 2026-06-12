---
title: "No Sidebar, No top bar after messing with Compize."
date: 2011-08-25
forum: Desktop Environments
---

### Post by Seegee on 2011-08-25
So I just installed Ubuntu about 2 hours ago and I have already managed to mess it up. I am a complete noob when it comes to linux and this is the first time I have ever used it so I dont know much. Anyway, I installed compize effects and it was pretty cool. I was messsing with the settings when i kind of messed something up. There was a thing where you switch from "Unity" to "Default" and i wanted to reset all the settings back to default so I changed it to default. After doing that, all my windows dissapeared, the side bar dissapeared, and the top bar dissapeared. Pressing alt + f2 does nothing. The only thing I can do is open a virtual terminal by pressing ctrl + alt + f1. In there, I have tried unity --reset and this is what it said: unity-panel-service: no process found. Its been like that for a half hour now and nothing has happened. Please help me.

Thanks.

---

### Post by Frogs Hair on 2011-08-25
You can try unity --reset from the recovery console . You can enter it by selecting it from the session list found under greeter box . When selecting your user name in the login screen the session list will appear directly below the greeter box .

From the same list you could try to login to Ubuntu classic or Ubuntu no effects . If your are successful open Compiz and enable the Unity plug-in restart and try to login to Ubuntu .

---

### Post by Seegee on 2011-08-25
the problem is that I set it to automaticly login so I dont see a login box...

---

### Post by Seegee on 2011-08-25
Wait, I found what you are talking about but whenever I select something else, it boots into normal mode. When I sellect classic, its the same thing, when I select recovery, its still the same thing.

---

### Post by Frogs Hair on 2011-08-25
Try Ubuntu no effects and run the command from there . Reseting from the recovery console usually does the trick .

Try running these commands from the recovery console .```
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
sudo reboot

```

---

### Post by KalChung on 2011-10-14
Had the same problem,  I tried googling a solution but all the solutions listed doesn't seem to work.

I finally figured out it was config related, took a little trial and error on my part.

Just thought I'd share how I got my desktop back. 

The short version is to remove the following folders in your home folder
[INDENT]**.compiz-1**[/INDENT]
[INDENT]**.config/compiz-1**[/INDENT]


Yes, they are both hidden folders.  If that doesn't work, the long work-around was the following:  (Basically just save your home folder delete it then login as root to recreate it.)

1.  [CTRL] + [ALT] + [F6]
2.  login as root
3.  rename your home directory:
[HTML]mv /home/paul /home/mybackup[/HTML]
4.  make a new home directory
5.  give yourself ownership of your directory
[HTML]chown paul:paul /home/paul[/HTML]
6.  [HTML]/etc/init.d/lightdm restart[/HTML]

You should be able to login again with the top and side bar available.  Once you've verified everything is there, copy all your settings back from backup folder  (/home/mybackup).

** this is only a workaround, if anyone figures out the **real** solution please let me know as well...

---

