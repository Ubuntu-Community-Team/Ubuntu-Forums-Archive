---
title: "Avast-What Happened?"
date: 2010-12-31
forum: Desktop Environments
---

### Post by AZinOH on 2010-12-31
Using this link  [http://www.avast.com/linux-home-edition#tab4](http://www.avast.com/linux-home-edition#tab4), I attempted to install Avast Linux on 2 computers:the older one dual-boots XP and was upgraded from 8.04 to 10.04. The newer one dual-boots Vista and had a clean install of 10.04. I used the same DEB package for both. The installs seemed straightforward, the program was found in the Accessories list and was run successfully on both machines. The problem is that after being rebooted, the program seems to have disappeared from the newer machine. It's as if it was never there. It is no longer in the Accessories list. The older machine is fine-Avast is still there. 

Thinking perhaps I did something wrong, I reinstalled Avast again on the newer machine. Again, it disappeared after the machine was rebooted. This computer is otherwise running normally and quite well, in fact. If I didn't do anything wrong...what could it be? Thanks for any assistance.

---

### Post by SnickerSnack on 2010-12-31
Have you tried running it from the command line?  Just because it's not in a menu somewhere, doesn't mean it isn't installed.

---

### Post by AZinOH on 2010-12-31
I would try to run it from the command line, but don't know what the command would be (still a Linux noob...sorry).

---

### Post by howefield on 2010-12-31
Try recreating the menu launcher for it via System > Preferences > Main Menu.

I don't know the command to start, but you can get that from the launcher in the other machine. Drag the menu launcher to the desktop, right click and select properties. You'll get the info you need and the path for the icon in there.

---

### Post by AZinOH on 2010-12-31
That solved the problem. Thanks for your assistance.

---

### Post by SnickerSnack on 2010-12-31
> **AZinOH said:**
> I would try to run it from the command line, but don't know what the command would be (still a Linux noob...sorry).

howefield is right, just look at the properties of the launcher on the other computer.  But, it's good to learn how to guess when that isn't available: try typing "avast" in the command line and then pressing Tab twice.  You may be given a few options on how to complete it.  If nothing else, just try "avast".

Also, googling "man avast" works, I found this: [http://ubuntuforums.org/showthread.php?t=449225](http://ubuntuforums.org/showthread.php?t=449225)

---

