---
title: "twinview move window to other screen"
date: 2009-02-26
forum: Desktop Environments
---

### Post by darkhammer8108 on 2009-02-26
I have been researching how to move a window from one screen to another in twinview and have come up with nothing. currently i am running xinerama which this works for but i cannot run compiz and i would like to have a config that i can show off to friends. i dont nessisarily need to grab the window and drag it thru the screen. if there is some sort of feature where i can say send to desktop x similar to have u can send windows to different workspaces in gnome that would work. i understand that when u use twinview these are separate x servers so if i click a link in pidgin it wont open if i have firefox open on the other screen. is there a workarond for problems like this as well?

---

### Post by Raistlin355 on 2009-06-14
Darkhammer, I saw your post and even though it is old I feel compelled to reply with my solution.  I have 3 monitors and use separate X sessions on them at first I made launchers to launch programs on the separate screens with the use of DISPLAY.  But then I install the Avant window manager and as it turns out if you make a launcher in Awn and then run it on each monitor the laucher will execute the program on the monitor you clicked the icon on.  Now this won't help you if you use the command line but it sure helped me out.  Good Luck!!!

E.G
```
 env DISPLAY=:0.2 xclock 
```
will start xclock on the second display

---

### Post by Chronon on 2009-06-14
I am not too familiar with how to set this up, but it's certainly possible. The default setup in twinview has the functionality you describe in Kubuntu Jaunty.  The two monitors provide viewports to a unified desktop space.  I can freely drag windows between monitors, even straddle them (though that's generally not desirable).

I'm sorry I don't know what to set, but this is exactly what my desktop system does.

---

### Post by Raistlin355 on 2009-06-16
> **Chronon said:**
> I am not too familiar with how to set this up, but it's certainly possible. The default setup in twinview has the functionality you describe in Kubuntu Jaunty.  The two monitors provide viewports to a unified desktop space.  I can freely drag windows between monitors, even straddle them (though that's generally not desirable).

I'm sorry I don't know what to set, but this is exactly what my desktop system does.

I am sorry, I don't fully understand your comment.  Are you wanting to use twinview? or are you wanting a separate X environment for your screens?

---

### Post by Chronon on 2009-06-17
No, I was responding to the OP (and others with the same question) that TwinView on my desktop machine does exactly what he wants. I.e. I can freely drag application windows back and forth between the two screens (as they simply function as adjacent viewports of the same desktop space).

---

### Post by Raistlin355 on 2009-06-17
Oh I gotcha, or course you can do that or use xinerama to span across all displays (in my case this didn't work too well cause I want to use compiz), but for me separate X screens works the best and I was just letting him (and the rest of the world know) about the solution I stumbled across.  :)

---

### Post by Chronon on 2009-06-17
Well thanks for that.  I learned something too!  :)

---

### Post by Monowai on 2009-06-19
I was gettin the "*Composite extension not availiable" [I]error*[/I].  Turns out I was using Xinerama which apparently Nvidia has no plans to enhance to support Compiz.  

so, after 
sudo nvidia-settings

I disabled Xinerama and *thought* I had enabled Twinview. After logging out & in I had 2 separate XScreens and couldn't drag apps across the windows (and my AWN didn't work either).

Going back in to nvidia-settings, I discovered Twinview wasn't enabled afterall.  After that and a reboot I now have wobbly windows and can drag and drop across both monitors on my logical desktop.

Not sure if this was User error or a glitch in nvidia-settings.  Still I'm a happy camper.  Off now to find out why my audio doesn't work!

hth

---

### Post by Zeobak on 2010-10-30
I cannot drag windows between monitors.  Don't know why not.  It is so aggravating to me that I can't do the simple action of dragging a window from one screen to another and none of the posts in this thread help at all.:mad:

---

