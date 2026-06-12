---
title: "Wine apps not showing in Xubuntu task list"
date: 2008-05-14
forum: Desktop Environments
---

### Post by Rmantingh on 2008-05-14
Why do applications running under Wine not show in my Xubuntu / XFCE4 task list?
All other applications show fine but not Wine.
It's quite annoying to 'lose' your wine apps behind other windows and having to minimize/close some to find them again.

Is this a Wine feature or is it Xubuntu?

Am I missing a setting somewhere?

---

### Post by dje on 2008-05-14
Open a terminal and type:
```
winecfg
```
Then in the 'Graphics' tab ensure that both tick boxes relating to allowing the window manager to control wine windows are checked then click apply and close the window. The windows should now appear in your task list

hope that helps,
dje

---

### Post by Rmantingh on 2008-05-14
I think my original question was misleading. Apologies for that.
There's something else wrong.
Some tasks DO show as buttons on the task list - others however don't.
I've heard somewhere say that it may be related to an icon problem?
For the task that does not appear I do not have a proper xpm icon.
Could that be the cause?
By ticking the "Emulate a virtual desktop" I can at least always see
a generic 'Wine' task on the task list which is at least workable.
I'll experiment a bit further.
Thanks for the help anyway.

---

