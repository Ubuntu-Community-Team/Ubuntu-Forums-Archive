---
title: "Can Unity run without Compiz?"
date: 2012-11-10
forum: Desktop Environments
---

### Post by DJS100 on 2012-11-10
I installed 12.04 couple of days ago, so I am playing with it.

What happens occasionally is that I receive the message "The application Compiz has closed unexpectedly." The options are to "relaunch" it, or "leave closed". When I just close the message without going for either of the options, Unity is still there, nothing actually crashed, as far as I can see. 

Then, when I wanted to check the Compiz options one time, I realized it was not actually installed on my system!

I thought the Unity can`t go without Compiz?

Can someone explain? Thanx.

---

### Post by jerome1232 on 2012-11-10
ccsm, or compizconfiguration manager is not installed by default, but compiz is. Unity doesn't play well with some of the other plugins and so ccsm has become a very unfriendly tool.

Unity does require compiz, although there is a unity 2d mode which doesn't use compiz, but if you were in Unity 2d compiz wouldn't be running to crash. Open your system monitor, you should see compiz listed in there as running.

---

### Post by COMECON on 2012-11-10
On Ubuntu 12.10 there's not Unity 2D anymore, so Unity will always run Compiz...  Unless your graphics card isn't supported by OpenGL/ES, then llvmpipe will be used for rendering and, AFAIK, it won't use Compiz.

---

### Post by grahammechanical on 2012-11-10
I tested 12.10 when it was being developed. We had many upgrades to Compiz - the compositing/window manager- that is. I often got that error message of Compiz closing unexpectedly. It says something for the robustness of Ubuntu that the whole OS did not crash.

As previously noted the reason that the OS did not crash was most likely due to llvmpipe being used as the fallback mode.

On 12.04 you still have the window manager for Unity 2D - metacity. This is most likely why your OS does not crash and you did not loose Unity. It most likely was then running as 2D.

A log out and log in can relaunch Compiz and Unity 3D

Regards.

---

### Post by mcduck on 2012-11-10
If any required component of the desktop environment crashes, Gnome will automatically attempt to restart it. (and Unity is still based on Gnome desktop, so this applies to Unity session as well).

Window manager (Compiz in this case) of course is a required component, so in most cases if it crashes it will simply restart immediately. Which is what you are seeing. :)

(of course it would make sense if the crash dialog would actually check if the program has already restarted successfully, and in that case wouldn't give you the pointless options to leave closed or restart...)

---

### Post by Oddbrid on 2012-11-10
With the help of Ubuntu Tweak you can disable Compiz in Ubuntu 12.04
But you wont feel any boost at all, you'll be really surprised xD

---

### Post by deadflowr on 2012-11-10
> **grahammechanical said:**
> 
As previously noted the reason that the OS did not crash was most likely due to llvmpipe being used as the fallback mode.


Would that be a good alernative to compiz, or rather something closer to a spare tire? In other words, something simply to help you get by temporarily.

For the record though, Unity is a plugin shell for compiz.

---

### Post by DJS100 on 2012-11-10
Compiz and CCSM are actually different, ok.

My system does not have separate graphic card, and after the installation it was running Unity fine.  So to check which Unity I was having I ran 
"echo $DESKTOP_SESSION " in the terminal, and it was reporting back unity, not unity2D. Then I found out about the  llvmpipe driver and the rendering it does for the environments without  separate graphics...

---

### Post by MG&amp;TL on 2012-11-10
It's possible that compiz had an internal error, but managed to recover. Although whether apport (the crash report window) would have picked it up or not is another story.

---

### Post by DJS100 on 2012-11-10
> **grahammechanical said:**
>  
As previously noted the reason that the OS did not crash was most likely due to llvmpipe being used as the fallback mode.

On 12.04 you still have the window manager for Unity 2D - metacity. This is most likely why your OS does not crash and you did not loose Unity. It most likely was then running as 2D.
 

I`m still not sure whether it`s compiz or metacity doing the managing.

---

### Post by zombifier25 on 2012-11-11
> **DJS100 said:**
> I`m still not sure whether it`s compiz or metacity doing the managing.

```
echo $DESKTOP_SESSION
```
If it returns ubuntu, then it's Compiz. If ubuntù2d, then Metacity.

---

