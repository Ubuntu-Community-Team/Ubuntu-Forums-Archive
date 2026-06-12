---
title: "Where did notifications after updates go?"
date: 2006-01-12
forum: Desktop Environments
---

### Post by nocturn on 2006-01-12
After my first install (upgrade), I got a notification with a little lightbulb in the notification area, it had a balloon popup saying that the installed upgrades (the kernel) required a reboot to be effective.

Since then, I have never seen that message again after kernel updates.

What happened to it? 

If it is still there, is there a way to use it for my own packages (I want to give users the message to log out and log back in on updates)?

---

### Post by manicka on 2006-01-12
Go to apps-->update-notifier in the Configuration Editor and check if the 'no_show_notifications' box is checked.

---

### Post by nocturn on 2006-01-12
[QUOTE=manicka]Go to apps-->update-notifier in the Configuration Editor and check if the 'no_show_notifications' box is checked.[/QUOTE]

Thanks, I'll do that

Any idea how I can trigger them myself?

---

### Post by lamego on 2006-01-12
You can't trigger the notifications, if the notification app is properly setup the icon will be shown when (and just when) new updates are available.

---

### Post by nocturn on 2006-01-12
[QUOTE=lamego]You can't trigger the notifications, if the notification app is properly setup the icon will be shown when (and just when) new updates are available.[/QUOTE]

I mean the warning that appeared after installing the new kernel, that says to reboot the system.  I want to give a similar warning asking the user to log out and back in.

---

### Post by justaguynpc on 2006-01-12
I, too, lost update notifier quite along time ago, not really understanding the reason why.  It could possibly had been because of a kernel update.  However, when I 

 "Go to apps-->update-notifier in the Configuration Editor and check if the 'no_show_notifications' box is checked" I see :

 Name: update_notifier
 Value: 0

in addition to a "warning" which states "This key has no schema"  (?)

Any ideas on how I go about re-initializing update notification?
What would be the proper "Value", a 1?  a -1?

I should add that I removed update notifier from my notification area, and never understood how to "get it back" because update-notifier is not a "default" option to task bar via "add to panel" menu.  I would like to get this cleared up if I could, am looking forward to any assistance in this matter.

Thanks

---

### Post by justaguynpc on 2006-01-12
I should add that I removed update notifier from my notification area, and never understood how to "get it back" because update-notifier is not a "default" option to task bar via "add to panel" menu. I would like to get this cleared up if I could, am looking forward to any assistance in this matter.


SOLVED : I was confused between update manager and update notifier.  I simply searched for update notifier under add to panel menu and voila : I have it back AND it is working. (Geez!)  :)

---

### Post by manicka on 2006-01-16
[QUOTE=nocturn]I mean the warning that appeared after installing the new kernel, that says to reboot the system.  I want to give a similar warning asking the user to log out and back in.[/QUOTE]
I'm pretty sure you can't customise that type of warning. It's seems to be only for kernel updates.

---

### Post by qferret on 2006-01-16
[QUOTE=manicka]I'm pretty sure you can't customise that type of warning. It's seems to be only for kernel updates.[/QUOTE]

I'm sure you can make your own though. How do apps such as GAIM put an icon in the tray?

---

