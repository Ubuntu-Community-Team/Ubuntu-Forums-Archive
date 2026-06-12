---
title: "The program &quot;Force Quit&quot; is frozen."
date: 2011-03-11
forum: Desktop Environments
---

### Post by Neogenics on 2011-03-11
So, I feel kind of retarded asking this. My situation is this. I have added to my Panel the "Force Quit" program to click and use so I don't have to type it in on the rare occasions that I need it. I accidentally clicked it today not needing it. Not knowing this would be an issue, I clicked on it thinking it would force itself to quit and just close itself. I know I should have just hit esc to close it.

The problem I have now is that it is now frozen on my screen and for the life of me I cant figure out how to get rid of it. Yes I tried esc. I tried opening System Monitor and looking for it to end the prog and couldn't find it. I know I could fix this by just restarting the x server, but at the moment I happen to have several things open that I either cannot save right now or are actively running.

So am I just stuck this way until I can restart the x server or is there another solution to this problem? I tried google. The problem with that is I am only able to find how to's on using the force quit to close other programs.

---

### Post by Tiiba on 2011-03-11
I know that I've clicked on that thing without trouble a hundred times.

Wouldn't know how to help.

---

### Post by Copper Bezel on 2011-03-11
This is hilarious, so thank you. = )

I imagine you've already solved this, but what you'd do is to run " xkill " and click on the window. I'm actually using this as a Compiz keystroke command in place of the Force Quit applet - more *certain*.

---

### Post by Neogenics on 2011-03-11
> **Copper Bezel said:**
> This is hilarious, so thank you. = )

I imagine you've already solved this, but what you'd do is to run " xkill " and click on the window. I'm actually using this as a Compiz keystroke command in place of the Force Quit applet - more *certain*.

Lol sadly. No it's still there on my screen. I tried xkill before i posted that and it didn't do anything. This wouldn't bother me as much except for the fact that it's stuck on top of all other programs too. So no just sticking it in the background and forgetting it. And it's on all the workspaces.

Edit
If it helps. I can open a new force quit to close other apps but the box is in the same spot as the old one so i can't click on the old one. I's almost like a ghost image of it sitting there. I tried restarting nautilus but that didn't work.

At this point I am determined to find out how to fix it just because it bugs me that I don't know how to.

---

### Post by Krytarik on 2011-03-11
It turned out that it isn't really a usual window, but if you restart gnome-panel, it should get killed:
```
killall gnome-panel
```

---

### Post by Neogenics on 2011-03-11
> **Krytarik said:**
> It turned out that it isn't really a usual window, but if you restart gnome-panel, it should get killed:
```
killall gnome-panel
```

THANK YOU. That did the trick perfectly. Only thing is I had to run nautilus to get that to start back up after I did the killall.

Thanks again for the help!

---

### Post by Krytarik on 2011-03-11
> **Neogenics said:**
> Only thing is I had to run nautilus to get that to start back up after I did the killall.

I didn't get that exactly. Didn't gnome-panel restart automatically, or what do you mean?

---

### Post by laceration on 2011-03-11
Congratulations, you have won the most ironical problem of the month award.  The award is a boxed set of "The Guide To Recursive Programming".

---

