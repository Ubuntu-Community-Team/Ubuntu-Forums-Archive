---
title: "tool bar vanished"
date: 2009-06-24
forum: General Help
---

### Post by saskatchewan on 2009-06-24
Ubuntu 9.04 AMD 64.

This morning when I turned on my computer there was not tool bar on the top.

I tried several restarts and I still can't find it.

It was there last night when I turned it off.

how can I get it back?

---

### Post by gettinoriginal on 2009-06-24
Are you talking about a panel ??  :confused:  If so, take your cursor to the top of your screen to make sure you didn't accidentally change it to auto hide, if it pops up, right click it and untick the autohide.

---

### Post by Gaweph on 2009-06-24
Im at work at present,

but dont worry, i think it s possible to add another panel.
All of the things on it are just panel add ons.  SO you ahvent lost anything, really.

Will check how to add a new one when i get home. and see if you still need help.

---

### Post by gettinoriginal on 2009-06-24
If you have a bottom panel, you can right click and choose "New Panel", then right click on that new panel and choose "Add to Panel"  :D

---

### Post by saskatchewan on 2009-06-24
I have no panel and when I go to the top there is nothing popping up.

---

### Post by gettinoriginal on 2009-06-24
Try opening a terminal and type ```
gnome-panel
```

---

### Post by saskatchewan on 2009-06-24
yes, this is really strange, if you can check when you get home that would be great.

---

### Post by saskatchewan on 2009-06-24
How do I get a terminal?

There is just the background for the screen and no icons at all?

---

### Post by Legace on 2009-06-24
> **saskatchewan said:**
> There is just the background for the screen and no icons at all?

Press ALT + F2, and type in:
```
gnome-panel
```

and tell if it helps.

---

### Post by saskatchewan on 2009-06-24
when I press alt + f2 it does nothing

Is there another way to bring up a terminal?

---

### Post by saskatchewan on 2009-06-24
this is nasty
I am wondering if I have to do a re install

---

### Post by saskatchewan on 2009-06-24
Well i tired a re-intall and that did the trick...  Until I restarted the computer then the same problem arose all over again.

Any suggestions?

---

### Post by starcannon on 2009-06-24
Try this link:
[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

GL

---

### Post by Leslie Viljoen on 2009-06-24
If alt-f2 doesn't work, I can't see how you are going to run anything without a panel. You can switch between text terminals and graphical terminal by pressing ctrl-alt-f1 and ctrl-alt-f7. Perhaps you can log in via the text terminal and then look at your xorg log files in /var/log.... IF ctrl-alt-f7 works!

You won't be able to run the panel from the text console though. Have you tried choosing a different window manager at the login screen?

---

### Post by starcannon on 2009-06-24
The ~/.* config files can be deleted by booting from a liveCD. Considering that everything works and looks like it should on the liveCD its most likely a hosed up config file in the /home/*usernamehere*. Try that guide, use a liveCD to get yourself a functional GUI to work in.

---

### Post by executorvs on 2009-06-24
I can think of a few possibilities
1. the graphics loading out of sync with your monitor. does your mouse scroll off the screen to the top or left sides?

2. as stated above configs not generated properly.

3. it may seem stupid to ask but does your keyboard have a F-Lock key and is it active. if it's not any command using the F-keys will not work.

---

### Post by saskatchewan on 2009-06-24
thanks for all the ideas.  Let me try them, it will take me a bit of time to catch up.

---

