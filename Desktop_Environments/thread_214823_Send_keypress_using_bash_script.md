---
title: "Send keypress using bash script"
date: 2006-07-13
forum: Desktop Environments
---

### Post by Lunar_Lamp on 2006-07-13
I set up xgl/compiz to work by selecting session on login.  Whilst I prefer this method as it is simpler to get back to a standard gnome session, there are two negatives I have noticed so far.  I have written a little script to allow me to click an icon to shutdown/reboot, so that's that issues solved.  the other issue is that when watching a DVD the screen keeps fading after about 5-10 mins unless I hit a key.

So, I decided I would try and write a little bash script that simulated a key-press which I could activate when I want to watch a DVD, but I'm not sure how to send a keypress signal using a bash script - all my googling keeps telling me how to detect a keypress, which I know how to do, heh.  I am very new to bash scripting, so hyper-complex guides are probably not going to help me out too much.

---

### Post by philippe_carlo on 2006-07-13
Of course, you could also pervent the screen from blanking under
System->Preferences->Power Management

---

### Post by Lunar_Lamp on 2006-07-13
I was under the impression that those settings were relevant to metacity etc, and therefore would have no effect with xgl/compiz.

---

### Post by philippe_carlo on 2006-07-13
But did it do the trick?

---

### Post by Lunar_Lamp on 2006-07-13
No :(

---

### Post by philippe_carlo on 2006-07-13
Try running this in the background

```

while true; do sleep 60; xscreensaver-command -deactivate; done

```

---

### Post by philippe_carlo on 2006-07-13
Which program are you using to watch video anyway? Normally when viewing videos, your screen should not blank out, because you enter a special display mode. Screen blanking is either caused by the screen saver or the power manager.

---

### Post by Lunar_Lamp on 2006-07-13
I didn't think this had anything to do with xscreensaver... I don't even have xscreensaver installed.

What you're written is pretty much what I wanted to do, but I wanted to have a keypress in there as opposed "xscreensaver -deactivate".

This is a known issue with using XGL/Compiz and affects all video watching programs - the solution I want to use is to the one I suggested as I think it is the only one that could work.

---

### Post by Lunar_Lamp on 2006-07-13
I think I may have an solution.

Install xautomation which simulates keypresses. 

The command ```
/usr/bin/xte "key Return"
``` returns a carriage return, i.e. simulates pressing of the key.  I will no experiment to see if this can be used to simulate user-input thus stopping screensaver.

```

#!/bin/sh

while true; do sleep 60;
/usr/bin/xte "key Return";
done
```

---

### Post by Lunar_Lamp on 2006-07-14
I haven't been able to get this to work.  The script does what it is supposed to do, but when I tried just opening it in a terminal in another window whilst watching a film, it would only run when the window was focused.

---

