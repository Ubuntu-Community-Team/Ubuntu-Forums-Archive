---
title: "Launcher and dock is gone."
date: 2011-05-24
forum: Desktop Environments
---

### Post by Thule on 2011-05-24
I installed the new ubuntu with unity.
I then used compizconfig to edit some stuff.
I wanted the launcher to be in the bottom and always show.

However, after I did this i ended up with:
[IMG]http://desmond.yfrog.com/Himg840/scaled.php?tn=0&server=840&filename=losteverything.png&xsize=640&ysize=640[/IMG]

Any ideas on how to fix this? I don't know how to open a terminal, a webpage since I don't have a dock or launcher.
I'm using ubuntu through classic now.

---

### Post by sikander3786 on 2011-05-24
Press Ctrl + Alt + F1 at the messed up desktop and login to the tty1 (terminal) window using your credentials. Then type this command:

```
unity --reset
```

Note: Running this command would reset all your Unity configuration to defaults e.g, Launcher behavior, icon size etc.

Wait for the command to finish. Once done, press Ctrl + Alt + F7 to see the desktop. Hopefully, it should be restored.

If not, please take a look at the troubleshooting guide here.

[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

---

### Post by Thule on 2011-05-24
> **sikander3786 said:**
> Press Ctrl + Alt + F1 at the messed up desktop and login to the tty1 (terminal) window using your credentials. Then type this command:

```
unity --reset
```

Note: Running this command would reset all your Unity configuration to defaults e.g, Launcher behavior, icon size etc.

Wait for the command to finish. Once done, press Ctrl + Alt + F7 to see the desktop. Hopefully, it should be restored.

If not, please take a look at the troubleshooting guide here.

[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

It worked, thank you very much

---

### Post by Copper Bezel on 2011-05-24
Go ahead and mark the thread as solved (Thread Tools in the upper right.) That helps the next person Googling for a solution to this problem. = )

---

### Post by Thule on 2011-05-28
> **Copper Bezel said:**
> Go ahead and mark the thread as solved (Thread Tools in the upper right.) That helps the next person Googling for a solution to this problem. = )

Thank you I didn't know how to do it :)

---

