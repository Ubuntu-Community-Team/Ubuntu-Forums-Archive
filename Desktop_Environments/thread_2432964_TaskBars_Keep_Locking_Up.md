---
title: "TaskBars Keep Locking Up"
date: 2019-12-11
forum: Desktop Environments
---

### Post by rebeltaz on 2019-12-11
I am running Ubuntu 18.04 LTS with gnome-session-flashback installed. Been working flawlessly ever since 18.04 came out. Now, all of a sudden, the upper ([Applications][Places].....[*]) and lower (running applications) taskbars are refusing to respond or update. I can still use the running programs (I am typing this in a locked up state); I can ctrl-alt-T to get to terminal and run programs directly (which is how I got firefox up to post this); I can alt-tab between running programs.... 

The only programs running when this happened were (the most current) firefox, (the most current) thunderbird, and (an older version) Ulimaker Cura. I thought it might be cura causing it, because that seems to always be running when this occurs - although I have been running this same version for over a year with no issues. I tried ctrl-alt-f2 to kill the cura process using [killall -9 cura], but while that did kill the process, I am left with a [cura.sh <defunct>] entry; the taskbars still won't respond or update; and cura is still shown in the taskbar. 

The only way out of this that I have found is to reboot. To my knowledge, nothing has been installed or updated since before this started happening. Does anyone happen to have any ideas?

---

### Post by CatKiller on 2019-12-11
I haven't used gnome of any sort for quite a while now, but ```
killall gnome-panel
``` might give your task manager enough of a kick to start behaving without having to do a full restart of the machine. I *think* it automatically respawns but, if it doesn't, ```
gnome-panel &
``` should start it again.

---

### Post by rebeltaz on 2019-12-11
If/When it locks up again, I will definitely try that. Thanks. Would still like to know why it keeps happening though....

---

### Post by rebeltaz on 2019-12-11
> **CatKiller said:**
> I haven't used gnome of any sort for quite a while now, but ```
killall gnome-panel
``` might give your task manager enough of a kick to start behaving without having to do a full restart of the machine. I *think* it automatically respawns but, if it doesn't, ```
gnome-panel &
``` should start it again.

OK.. it is locked up now. I tried doing as you suggested and issuing the killall command did not kill the gnome-panel instance. I am able to verify this through ps -A. I even tried adding -9, but that didn't kill it either. 

Something else that I've noticed that might add another clue to this mystery... I went to click on the [Reply With Quote] button here on the forums and when I did, it accepted the click, but it was as if I were holding the left mouse button down - the button was dragged around as I moved the mouse until the page loaded....

---

### Post by rebeltaz on 2020-01-03
So this is still happening if someone could help me diagnose it?

---

### Post by vanadium on 2020-01-03
Although this does not solve the issue, it can help isolating the issue: does it work again after restarting gnome shell, i.e., hit Alt+F2, type "r" and press "Enter". Can you certify that you are only using officially supported Gnome-Shell extensions? If you use third party extensions (i.e., installed from the Gnome Shell Extensions website) then disable them all, and see if the issue is gone. If yes, then enable one by one to find the faulty extension.

---

### Post by rebeltaz on 2020-01-03
> **vanadium said:**
> Although this does not solve the issue, it can help isolating the issue: does it work again after restarting gnome shell, i.e., hit Alt+F2, type "r" and press "Enter". Can you certify that you are only using officially supported Gnome-Shell extensions? If you use third party extensions (i.e., installed from the Gnome Shell Extensions website) then disable them all, and see if the issue is gone. If yes, then enable one by one to find the faulty extension.

To my knowledge/memory, I haven't installed any gnome shell extensions at all.

When I press Alt+F2, it pulls up the drop down [Application] menu pn my top taskbar. Hitting 'r' and 'enter' doesn't do anything.

---

### Post by vanadium on 2020-01-04
You meant that Alt+F1 is pulling down your application menu.

---

### Post by rebeltaz on 2020-01-09
> **vanadium said:**
> You meant that Alt+F1 is pulling down your application menu.

I'm sorry... you're right. I'm an idiot. I was hitting the wrong key. When I hit the right key, I got the window you were telling me to use. 

My taskbars are locked up right now, so I tried hitting Alt-F2 (making sure I hit the right key sequence this time) and nothing happens. That window doesn't come up. My only option is to hit Ctrl-Alt-T and issue either a 'reboot' or 'shutdown' command in terminal.

---

### Post by rebeltaz on 2020-01-11
OK... so...   **-=[UPDATE]=-**

Today, for some reason, the top panel (the one with [Applications][Places][*]) _partially_ locked up. I could still access all of the quickstart icons and the [*] shutdown menu, but [Applications] and [Places] wouldn't open. I tried [Alt-F2][r][enter] and it just told me that there was no [r] command. Looking around, I found that I could run [killall gnome-panel] to supposedly kill the panels and they would restart. Well, they shut down all right, but didn't restart. I had to do a [Ctrl-Alt-T] to get to the terminal and run [bohup gnome-panels &] to get them back. Once they were running again, I could again access both. 

This is really getting old and any help anyone has on how to diagnose this would be **_GREAT_**!

---

### Post by CatKiller on 2020-01-11
I still don't use Gnome, so I can't help you with the problem, but I can say that you can run the two commands together to save yourself some small annoyance;

```
killall gnome-panel && gnome-panel &
``` will kill the panels then, if that succeeds, launch them again - in the background so that you shouldn't need to keep your terminal window open.

---

### Post by rebeltaz on 2020-01-16
Well... new piece of the puzzle. Both top and bottom task bars are locked up. I tried the [killall gnome-panel] trick again, but this time, the task bars aren't dying. I tried running that with -9. I tried running it as sudo... nothing. So that works when only the top bar is frozen, but not when both are.

I cannot believe that I am the only one this has ever happened to. Who am I kidding? I **_only_** have issues no one else has ever had.....

---

### Post by rebeltaz on 2020-02-16
ummm... it's the dangdest thing, but.... I think I figured this out. I think my laptop was overheating. I noticed that the temperatures were running about 60°c which I didn't remember being abnormal, but then I saw that when Cura or FreeCAD were running, that would jump up to 80° at times. That, I knew was wrong so I took it to the shop and blew it out. Now, it runs between 36° and 60° at all times and has not locked up one single time since. 

My (rhetorical) question, though is why would **only** the taskbars lock up while everything else continued running normally? I mean, I did not change or do anything else that could account for it not locking up anymore, so that has to be it... it just doesn't make sense. 

Anyway... thank you all for your help.

---

