---
title: "Some window management program not running, help me find it"
date: 2012-04-09
forum: Desktop Environments
---

### Post by bjherbison on 2012-04-09
Many window controls don't work: alt-space does nothing, window menus aren't working, I have one work space instead of multiple, I'm having focus issues.

What XFCE program is missing and how do I get it started / set to start automatically again?

More details:

Using XFCE on 10.10. Everything has been working well for a while, no recent upgrades. Some windows hung so I restarted (from the menu, not the power button) without closing running applications.

Now several strange things happen when I log in.


[LIST]
[*]Before my background would start with a pink design, switch to a blue xfce background, then turn to a different pink design. Now it stays blue.
[*]Program windows from my previous session appear, all in the upper left.
[*]The window controls are missing -- the border with minimize, maximize, menu, etc is gone.
[*]alt-space M doesn't let me move windows, I just get "m" in the application window.
[*]There are focus issues, some parts of applications can't get focus.
[/LIST]
I could give more details, but that's probably enough.


What program isn't running?  How do I get it running, and keep it running?


Thank you for your help.

---

### Post by Bucky Ball on 2012-04-09
Have you switched off and switched machine back on or just been logging out and back in?

---

### Post by bjherbison on 2012-04-09
> **Bucky Ball said:**
> Have you switched off and switched machine back on or just been logging out and back in?

I rebooted the machine and that didn't change the situation.

---

### Post by brainwash on 2012-04-09
Looks like the current xfce session gets restored on every startup. However, the window manager (xfwm4) seems no to be running.

So navigate to Settings Manager > Session and Startup and disable the "Automatic save session on logout" option. Also remove the content of ~/.cache/sessions.
```
rm -r ~/.cache/sessions
```

---

### Post by bjherbison on 2012-04-09
> **brainwash said:**
> Looks like the current xfce session gets restored on every startup. However, the window manager (xfwm4) seems no to be running.

So navigate to Settings Manager > Session and Startup and disable the "Automatic save session on logout" option. Also remove the content of ~/.cache/sessions.
```
rm -r ~/.cache/sessions
```
Thank you, brainwash, removing the sessions directory fixed the problem.

Interestingly enough, "Automatic save..." was not checked even though previous sessions were being ignored.

Something's still not running the same as before as the last transition from a blue xfce background to the pink background didn't happen. I don't care (and I won't care until I find something that doesn't work right).

By the way, typo in my initial post: I'm running 11.10, not 10.10. Fortunately that misdirection didn't seem to slow down the process of getting help.

---

### Post by brainwash on 2012-04-09
You have to provide more details to solve the pink background mystery.Maybe the background color drawn behind the wallpaper got somehow changed (Desktop Settings > Background)? Or did you install another application like Nautilus which might interfere with the XFCE desktop manager?

---

### Post by lemonbar on 2012-04-10
I was having this problem too, and removing the sessions cache worked - thank you so much:KS.  
But... why do saved sessions break the windows on the next start up? I'm running Ubuntu Studio 12.04, which uses xfce4.

---

### Post by bjherbison on 2012-04-11
> **brainwash said:**
> You have to provide more details to solve the pink background mystery.Maybe the background color drawn behind the wallpaper got somehow changed (Desktop Settings > Background)? Or did you install another application like Nautilus which might interfere with the XFCE desktop manager?
Interestingly, it's back. I haven't had time to experiment. All I did was boot, run my standard programs, shutdown to sleep or go to work, repeat.

This morning the pink is back, and right-click/Change Desktop Background shows me I have the pink image selected as wallpaper. I find it mildly interesting that it didn't show up on the first or second boot after I cleared my session date--interesting enough to come and mention it here, but not interesting enough to go and figure out why (I have too many other interesting things to investigate).

Thanks again for your assistance.

---

### Post by auton on 2012-06-18
I'm having a similar problem; xfwm4 doesn't seem to revive along with the session. 

Mind I am running Linux mint, and will post in those forums, but it's a serious and annoying problem and needs attention.

---

### Post by Bucky Ball on 2012-06-18
Welcome.

Suggest you start a new thread with a descriptive title. This one has been dead for  two months so you probably won't get much help here (and this thread details the specific issues of another OP which don't seem to be the same as yours). ;)

---

