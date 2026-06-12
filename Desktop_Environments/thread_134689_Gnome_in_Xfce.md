---
title: "Gnome in Xfce"
date: 2006-02-22
forum: Desktop Environments
---

### Post by metro.tramp on 2006-02-22
I've just been playing around with xfce, and like what i've seen. However, i really need to start doing a little research into apps and utils for it. At the moment, i'm mostly using those i already have installed for gnome, which has led to a bit of a problem.

I was having issues with my second hard drive, and in the process of mucking about with it, i used the 'disks' util from gnome. i happened to click on the 'browse' option. only after i clicked did i figure it'd open up the gnome file manager rather than the xfce one; which it promptly did, along with the gnome background, and (it seems, some of the desktop).

to compound the problem - i had xfce set to autamically save sessions on logout, so when i restarted, hoping that it'd all be fine afterwards (it always works with windows!! :( ) it.. well.. did the obvious and stayed the same (damn reliable linux..)

so now i have a gnome background which has the gnome options when i right click instead of the xfce menu, and it's all wrong... :cry: 

so can anybody help me get back to the normal xfce desktop?


while i'm at it, i might as well ask some xfce questions that've been bugging me... is there any way to set xfce to auto login, instead of having to choose session and login everytime? is there any way to 'bind' the two bars together to have a single bar for all tasks?


thanks

---

### Post by kaamos on 2006-02-22
Alt+F2:
```
killall nautilus
```
And again Alt+F2
```
xfdesktop
```

For the panel thing, kill the process of the upper panel (can't remember the name right now) and add the stuff you like to the lower panel.

Hope this helps!

---

### Post by bimargulies on 2007-12-30
I'm having the same problem, and the response didn't respond to the most mysterious part.

Every time I log in, I get a set of gnome processes. I have my preferences set to turn OFF gnome support. I have my sessions set to save-on-exit. I checked the files in .config, and I can't find the source of these processes. But they keep coming back (gnome-screensaver, gnome-power-manager, etc).

---

