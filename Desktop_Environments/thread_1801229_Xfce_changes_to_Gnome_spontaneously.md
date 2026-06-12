---
title: "Xfce changes to Gnome spontaneously"
date: 2011-07-10
forum: Desktop Environments
---

### Post by berlinick on 2011-07-10
Dear Forum members!

Here's the thing: When I work in Xfce session or in Xubuntu session (10.10 on Acer Aspire One) the whole DE switches from Xfce to Gnome. I see it not only on the change of the desktop wallpaper, but on application menu, context menu etc. It changes from my Xfce setup, which I know and love, to Gnome and then back in some 1 to 3 second interval. It switches back and forth untill it finally stays on Gnome. I love Gnome, but would like to have working Xfce on *this* machine.

I googled for similar problems and possible solutions before posting here, but wasn't successful. All inputs will be very much appreciated.

Have a nice day! :)

---

### Post by koleoptero on 2011-07-10
Unfortunately I don't remember the specific names of the applications in xfce but...

There is a session tool somewhere in the xfce settings manager. If you open it you'll see in a tab it has the options to start the gnome services on login. Check to see if it is selected and if it is remove it and logout+login.

If it isn't selected then check to see if nautilus starts at some point on startup because of some reason. It is possible that some folder shortcuts on the desktop or the panel could be launching nautilus instead of thunar. I'm afraid if such is the case I don't remember how to make them open them with thunar.

---

### Post by berlinick on 2011-07-10
Hey, thanks for the fast reaction!

I tried the first solution. Starting GNOME Services was checked, so I uncheked it, but it didn't solve the problem.

I was trying to kill nautilus, but it was starting again right after it.

It is stupid, but I'm still learning to remember the solutions I find spontaneously :) I believe however, this is what did the job:

[http://forum.xfce.org/viewtopic.php?id=3229](http://forum.xfce.org/viewtopic.php?id=3229)

See the reply from TomE:
```
gconftool-2 --type=bool --set /apps/nautilus/preferences/show_desktop 'false'
```

---

### Post by koleoptero on 2011-07-10
Well at least you found a solution :) Nautilus shouldn't be starting anyway but who knows why it does... Check your startup applications again to see if there's something responsible for it there.

---

### Post by berlinick on 2011-07-10
That's a part of the problem: Nautilus isn't among the applications started on start up (at least not in the Xfce Settings Manager) and I can't find a way to delete nautilus from the session other then by killing the process, which I did about a dozen times with no effect. But, as you said, the problem is solved. Thank you again!

---

