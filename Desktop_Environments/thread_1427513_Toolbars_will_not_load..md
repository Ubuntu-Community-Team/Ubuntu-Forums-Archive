---
title: "Toolbars will not load."
date: 2010-03-11
forum: Desktop Environments
---

### Post by mindsize on 2010-03-11
Hi, I'm new to Ubuntu and not really sure how to dignose this problem.  What is happening is when i start up Xubuntu 9.10 the spinning wheel will not go away and when i open up any windows the header does not load (so i can not move or close that window.)  The system was running fine until i started messing with Compiz, so i messed something up.  Now i just have to figure out what and how to undo it : )  So i ran all the system updates.  No change.  Uninstalled anything with the keyword compiz that came up in the package manager.  Still no change.  Disable and reinstalled my video driver... nothing.  When i did run my last set up updates, during a reboot i got a message about starting up in, something like, simple video mode...i forget the exact wording, but the system started up fine and all the windows tool bars worked.  The next time i rebooted though things went back to not loading properly.

So i guess my 2 questions are
1. is there any system restore function on Xubuntu and/or
2. how would i go about dignosing what is causing this hangup.

Again i'm sorry for basic understanding of Xubuntu and would appresiate any direction.
Thanks

---

### Post by denham2010 on 2010-03-12
Hi,

This is quite a simple thing to fix, but first, a little explanation, just so you understand why this happened.

With Linux, graphical desktops are actually made up of multiple parts. The main ones being the desktop itself and a window manager.

The desktop, in your case Xfce controls the basic operation of your desktop including the theming of your windows (everything inside the frame of a window) and the widgets (buttons, scroll bars etc), mouse theme, desktop theme and colours etc.

The window manager controls the behaviour of windows (re-size, minimise & maximise etc) along with theming the window frames (borders, title bar etc).

The default window manager for Xfce is xfwm4. Now here is where your issue has occured. Compiz is also a window manager. So when you experimented with that, you replaced xfwm4 with compiz. Now that you have removed compiz, you haven't told your system what window manager to use, hence you no longer have your title bars etc.

To fix this, you simply need to run xfwm4 again either in a terminal, or by pressing ALT + F2 and entering the following:

```
xfwm4 --replace &
```

You will notice this is very similar to the code you would have entered to start compiz.

So when ever you wish to try a different window manager (most common ones are xfwm4 - xfce, kwin - kde, metacity - gnome, compiz - all desktops and soon to be released gnome-shell - gnome, among many others which are favourites to many users), you generally enter:

```
<window manager command> --replace &
```

to start it, and

```
xfwm4 --replace &
```

to return to your default (in this case default for xfce).

Hope this helps!

Cheers.

---

### Post by denham2010 on 2010-03-12
Now, regarding the system apparently hanging on boot:

Once the system has started, open a terminal and enter the following:

```
dmesg
```

A lot of information will scroll by. This is basically a 'log' of what is happening when you boot your computer.

Since the 'hanging' seems to occur when you log in, have a look right at the bottom of the output to the dmesg command.

I know you are new, so a lot of the output may seem indecipherable, but it may give a clue to what is happening (an error message for example).

If you can't seem to locate any issues, or just aren't sure, post a copy of the output of the dmesg command in here so others can have a look.

Cheers.

---

### Post by mindsize on 2010-03-12
Hey, thank you for such a quick and detailed response.  It really helps that you took the time to explain the reason behind the problem rather than just giving me terminal command to enter!  This worked perfectly and makes a lot of sense now. 

In regards to the system hang, it wasn't so much that anything was freezing, it's just that the spinning wheel never went away.  I was still able to do everything fine. I'm assuming the spinning wheel had to do with the system was looking for the xfce files because now I replaced it there is no more spinning wheel.

Thanks again!
-Asher
[www.mindsize.us](www.mindsize.us)

---

