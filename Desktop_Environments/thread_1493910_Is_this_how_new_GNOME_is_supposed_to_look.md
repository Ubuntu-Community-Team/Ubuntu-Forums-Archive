---
title: "Is this how new GNOME is supposed to look?"
date: 2010-05-26
forum: Desktop Environments
---

### Post by SuperTeece on 2010-05-26
See screenshot attachment. I know there was going to be changes to GNOMES appearance, but I thought it was just moving Close/Maximize/Minimize to the other side.

If the screenshot is correct I'll just adapt and move on, if not how do I fix it?

---

### Post by drpjkurian on 2010-05-26
Hi
I see that you do not have any of the buttons. It can be solved by following procedures

1. Downgrade the visual effects to 'none'

2.Disable compiz

---

### Post by SuperTeece on 2010-05-26
> **drpjkurian said:**
> Hi
I see that you do not have any of the buttons. It can be solved by following procedures

1. Downgrade the visual effects to 'none'

2.Disable compiz



Effects were already to None. In terminal I tried ```
metactity --replace
``` which caused the terminal window to have the buttons and be moved, closed, resized. I close terminal and come back to firefox and have same issue.

---

### Post by Barafu Albino Cheetah on 2010-05-26
You have one of the tw possible compiz problems. Install following packages: compizconfig settings manager and fusion-icon. The latter resides in "System" menu and can help you to manage all effects. 
Make sure you have metacity as your window decorator and compiz as window manager.
In compiz settings make sure you have "Window decorator" plugin enabled for any window type. 
Switch metacity with emerald to and fro several times. It really helps. 
By default, emerald has no themes installed. In this case it shows no window borders.

---

### Post by Seq on 2010-05-26
> **SuperTeece said:**
> Effects were already to None. In terminal I tried ```
metactity --replace
``` which caused the terminal window to have the buttons and be moved, closed, resized. I close terminal and come back to firefox and have same issue.

metacity was running within your terminal. Closing your terminal kills metacity. A trailing ampersand will disconnect it from the terminal:

```
metacity --replace &
```

As to why it is not running at login, I'm not sure. I'm sure somebody else will know the right gconf setting to poke.

---

### Post by SuperTeece on 2010-05-27
So I installed the packages and had little success.. but kept playing around. After following your steps, all windows expect Firefox now had the buttons. In Firefox I had to go to File>>New Window then close the whole program with file>>quit and re open. Seems fine now.

---

