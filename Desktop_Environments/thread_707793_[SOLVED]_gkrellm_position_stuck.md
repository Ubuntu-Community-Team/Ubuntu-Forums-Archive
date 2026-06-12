---
title: "[SOLVED] gkrellm position stuck"
date: 2008-02-25
forum: Desktop Environments
---

### Post by Bob Burks on 2008-02-25
I have had gkrellm installed and working fine, but lately it appears in the upper left corner of the screen.  Nothing I can do seems to be able to move it anywhere else.

I would like to dock it to the right side of the screen.

Help much appreciated.

---

### Post by linuxwizard on 2008-02-25
Have you tried > right click on Gkrellm > configure > click on General > Option tab & Properties tabs> look over settings > some are for screen & dock options

---

### Post by Bob Burks on 2008-02-26
Thanks.  Tried that.  Nothing I can do causes it to be moved.

---

### Post by linuxwizard on 2008-02-26
If you can't drag Gkrellm across your desktop and place it where you want and you checked your settings, not sure what else to tell you. I have been using Gkrellm for some time now both Kubuntu & Ubuntu and not had or seen this issue before.

---

### Post by ayoli on 2008-02-26
You may want to use the -g switch with a position, here's how I launch gkrellm on the right of my screen :
```
gkrellm -g +1198+268 --wm
```
first integer value is x (horizontal) position, second is y position

---

### Post by yabbadabbadont on 2008-02-26
> **Bob Burks said:**
> I have had gkrellm installed and working fine, but lately it appears in the upper left corner of the screen.  Nothing I can do seems to be able to move it anywhere else.

I would like to dock it to the right side of the screen.

Help much appreciated.

What window manager are you using?  How did you launch gkrellm?

If you are using Fluxbox, Openbox, Blackbox, WindowMaker, ...  they all have a dock area (called the slit in fluxbox).  If you started gkrellm with the "-w" option (withdrawn), then it will only appear in the dock and cannot be moved from it.

---

### Post by Bob Burks on 2008-03-03
I had to give up and do the simple thing of uninstall gkrellm then reinstall it.  Now I can change the positon.  Have no idea why, but it worked.

Many thanks for the help, Folks.

---

### Post by linuxwizard on 2008-03-03
Well glad to hear you got Gkrellm working and you can adjust the position you want. Please mark thread as SOLVED.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by nickpaton on 2008-03-31
I know this is marked as SOLVED, however I've had the same problem using Xubuntu which has the xfce desktop.

Gkrellm was fixed in the wrong position and using Ayoli's suggestion was only a partial success.
This was because Gkrellm had a max/min/delete top panel at the top when the command was run, which subsequently disappeared on the next boot, leaving a panel sized gap at the top.

The solution I found was to go to Applications > Settings > Window Manager Tweaks > Accessibility tab and note the setting for 'key used to grab and move window'.  Mine was set to 'Alt' (key).

Hover over the Gkrellm window and press Alt and left mouse keys together, which will allow Gkrellm to be moved around the Desktop.

HTH

---

