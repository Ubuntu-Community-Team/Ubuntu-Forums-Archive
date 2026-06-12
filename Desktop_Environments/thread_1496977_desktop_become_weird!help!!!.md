---
title: "desktop become weird!help!!!"
date: 2010-05-29
forum: Desktop Environments
---

### Post by elfeight on 2010-05-29
[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG]help! my desktop accidently become like this:
[ATTACH]158754[/ATTACH]
i can't find the favourites, internet, system, etc to start the application...what should i do to return the desktop with default setting....pleasee...

---

### Post by wojox on 2010-05-29
Try running these two commands:

```

gconftool --recursive-unset /apps/panel
pkill gnome-panel

```

You may need to uninstall the mac4lin theme.

---

### Post by lisati on 2010-05-29
> **elfeight said:**
> help! my desktop accidently become like this:
[ATTACH]158754[/ATTACH]
i can't find the favourites, internet, system, etc to start the application...what should i do to return the desktop with default setting....pleasee...
Were you playing with themes? I notice an Apple icon on the top panel........

---

### Post by Timmer1240 on 2010-05-30
Left click panel add to panel scroll down and add menu bar!My desktop has become weird to but everything still works!

---

### Post by elfeight on 2010-05-30
> **wojox said:**
> Try running these two commands:

```

gconftool --recursive-unset /apps/panel
pkill gnome-panel

```You may need to uninstall the mac4lin theme.

i've already do that, but nothing happen... the desktop not change.

> **Timmer1240 said:**
> Left click panel add to panel scroll down and add menu bar!My desktop has become weird to but everything still works!

how do you that? please tell me...i don't understand....

---

### Post by Timmer1240 on 2010-05-30
Left click on the top panel select add to panel it should bring up a box scroll down and add menu bar looks like you have custom menu in the top left corner.Not sure if this will help you but give it a shot.

---

### Post by elfeight on 2010-05-30
can you give me the tutorial with screenshot? because when i click the top panel nothing happen...thanks...

---

### Post by alexorghici on 2010-05-30
uninstall the mac4lin theme because it does not work well in ubuntu 10.04

---

### Post by Timmer1240 on 2010-05-30
I dont think what I told you to do will help you sorry.you may have to uninstall any custom themes you have applied sounds like that is the source of your problems.

---

### Post by elfeight on 2010-05-31
okay, thanks for your advice...
maybe i'll re-install my Ubuntu 10.04...
thanks for all... :popcorn:

---

### Post by cascade9 on 2010-05-31
> **lisati said:**
> Were you playing with themes? I notice an Apple icon on the top panel........

I cant think of any other way that the average user is going to get the apple logo there. 

@elfeight- if you have installed an aple style theme, that could explain why you lost a panel, etc. Try changing to a different theme. ;)

---

