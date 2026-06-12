---
title: "NVIDIA Setting Panel Reduces CPU?"
date: 2007-04-24
forum: Gaming &amp; Leisure
---

### Post by GSF1200S on 2007-04-24
For some reason, if I attempt to run a OpenGL game, my cpu usage skyrockets to 100%. But, if I open and close the NVIDIA X-Window settings manager first, my cpu usage will stay down around 25-30%!! 

This doesnt make any sense to me. The game runs just fine either way- if I dont open the Xwindow, my fan comes on high and the cpu usage is high, and if I do, its just the opposite.

What the heck could be causing this?

Another thing thats weird: take open arena for instance. Whenever im at a menu, my CPU usage is at 100%. As soon as I enter the GAME it goes DOWN (!). This is regaurdless of the NVIDIA panel being opened or not. If I dont open it, CPU usage is high both in the menus and the game...

---

### Post by buttons on 2007-04-24
> **GSF1200S said:**
> For some reason, if I attempt to run a OpenGL game, my cpu usage skyrockets to 100%. But, if I open and close the NVIDIA X-Window settings manager first, my cpu usage will stay down around 25-30%!! 

This doesnt make any sense to me. The game runs just fine either way- if I dont open the Xwindow, my fan comes on high and the cpu usage is high, and if I do, its just the opposite.

What the heck could be causing this?

Another thing thats weird: take open arena for instance. Whenever im at a menu, my CPU usage is at 100%. As soon as I enter the GAME it goes DOWN (!). This is regaurdless of the NVIDIA panel being opened or not. If I dont open it, CPU usage is high both in the menus and the game...

The nvidia panel is a strange animal.  Before you open it, X has no knowledge of any settings you may have set in the panel.  So your disparity there is very likely due to some setting you think you've set, but haven't.

Fortunately there's an easy way to fix this, and that is to open your session manager of choice and add the following startup command to it:

```
nvidia-settings --load-config-only
```

Which loads your settings without bothering you further.

---

### Post by GSF1200S on 2007-04-24
> **buttons said:**
> The nvidia panel is a strange animal.  Before you open it, X has no knowledge of any settings you may have set in the panel.  So your disparity there is very likely due to some setting you think you've set, but haven't.

Fortunately there's an easy way to fix this, and that is to open your session manager of choice and add the following startup command to it:

```
nvidia-settings --load-config-only
```

Which loads your settings without bothering you further.

Where am I going to put this command? Usually to do a startup serice I would create a script and run that in services... but I dont know what to do here.

Still doesnt seem to explain why the cpu usage is higher in a menu than in the actual game.

Thanks very much for the code.

I get the idea even the Nvidia card is less supported than on windows.. its bs!

---

### Post by aidanr on 2007-04-25
system > preferences > sessions

add *nvidia-settings -l* reboot and see if it makes a difference

---

