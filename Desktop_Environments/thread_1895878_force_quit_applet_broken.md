---
title: "force quit applet broken"
date: 2011-12-15
forum: Desktop Environments
---

### Post by Byb on 2011-12-15
Hello
In Oneiric with gnome-panel I have the force quit applet in the panel (added  with alt+rightclick). Unfortunatly when I use it, the session hangs and  I just can switch CtrlAltF1/F7 but I don't know the name to killall the  kill applet. Please help. The applet makes a cross like a big thin [SIZE=3]**+**[/SIZE] sign.  I  tryied altF2 xkill it works (the cross is a thick **X** but my mum can't do that
The force quit applet worked before in maverick. I must use gnome-panel because unity is not good for my old pc.
I don't know the real english name for the applet. In french it is "Forcer à quitter" and the icon is a broken window.
And Escape won't work to recover keyboard/mouse usage: the + cross remains on screen & every thing in tty7 is locked
Could you tell me more about the old good applet please
Thanks

---

### Post by Rodney9 on 2011-12-15
Open a terminal and use ```
xkill
```

---

### Post by Byb on 2011-12-16
100 beans less :P
Did you read what I wrote: I know that but my mum can't do that because opening a term is out of scope to targeted ubuntu major audience : the newbs that will stay newbs. Windows has ctrl Alt Del and even that is too complex for a lot a users. But it also has warning popup with buttons "Application is unresponsive: kill | cancel(let run)". At least there was a working panel applet in ubuntu that could be added to panel.
A chance if a ubuntu basic user has in his friends or family someone that can create for him a launcher for xkill, but don't you think that little more skilled user that can do that has something else to do to spend their time than reinvent the wheel on each release?

---

### Post by stinkeye on 2011-12-16
An ubuntu basic user wouldn't be using gnome-panel on Oneiric unless
someone set it up for them.

---

### Post by Byb on 2011-12-16
My mum rather likes old things that work than new ones that don't

---

### Post by jimmydean886-2 on 2011-12-16
Huh. Cause Unity's always worked better for me. Doesn't matter.

So, you're saying that your mom can't handle typing "xkill"? No problem. Just go into the "Add Panel Applet" menu, and add a new custom launcher. Then, set the icon to the broken window (not sure where that is) and type xkill as the command. Name it force quit and you're done.

Hope this helps!

---

### Post by stinkeye on 2011-12-16
Some things don't work as before because of the change to gnome3 
and the new desktops but the customization features will come back as they develop.

In the meantime you can use the attached archive to create a force-quit launcher.
Uncompress and move the **X-Quit.desktop** file to **~/.local/share/applications**
Then drag the **X-Quit.desktop** file to gnome-panel.
It will show a notification when clicked on.

P.S. When I was 18 and unemployed my mother used to say 
she didn't like young things that don't work.

---

### Post by Byb on 2011-12-16
Thanks boy.... a chance I'm not so young myself (~50). The story is also that install gnome-panel was my one-shoot job, when altF2 xkill could be a dayly (mmmm, say monthly, the time to forget) for her... for me too ;) old things loose memory

---

### Post by Byb on 2011-12-21
I made a nice xkill launcher (means with a nice ?kill? icon) for her that replaces the supplied broken applet. Works for me too :)
Should I post a bug to launchpad?

---

