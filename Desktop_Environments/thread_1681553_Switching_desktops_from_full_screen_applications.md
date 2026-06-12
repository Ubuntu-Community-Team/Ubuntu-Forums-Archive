---
title: "Switching desktops from full screen applications"
date: 2011-02-04
forum: Desktop Environments
---

### Post by Eclipticon on 2011-02-04
Hi,

I'd like to run a number of applications full screen (e.g., VirtualBox, Vendetta Online) but I'd also like to switch to my other Gnome Desktops easily. 

Unfortunately, these applications seem to intercept my default and all other hotkeys I have tried for switching desktops ... I know there is a solution for VirtualBox via the host key, but I am looking for something more "generic".

Is there, for example, any way to catch key strokes in Gnome/Compiz before the full screen app receives them? 

Thanks!

---

### Post by 3Miro on 2011-02-04
Compiz does catch the key-strokes before the full screen app. I can switch between full screen app all the time. The issue with VirtualBox is that VB works with the kernel and it catches the key-stroke before it reaches Compiz. This is due tot he mechanics of the Virtual Box, I don't think there is a solution there.

I am surprised about Vendetta not working. Are you using wine or VirtualBox. I can workspace-switch full screen apps in Compiz with wine without a problem.

---

### Post by Eclipticon on 2011-02-04
Hi,

> **3Miro said:**
> I am surprised about Vendetta not working. Are you using wine or VirtualBox. I can workspace-switch full screen apps in Compiz with wine without a problem.

neither wine nor VirtualBox: Vendetta Online offers a native Linux version ... which in full screen mode seems to see the keys before Compiz, unfortunately.

---

### Post by nick_goodfate on 2011-02-04
You can set a screen edge binding for expo plugin of Compiz.

---

### Post by 3Miro on 2011-02-04
Check to see if the compiz shortcut corresponds to a shortcut in the game. If so, change either one of them.

---

### Post by Eclipticon on 2011-02-04
> **nick_goodfate said:**
> You can set a screen edge binding for expo plugin of Compiz.

Thanks nick_goodfate, this works very well for VirtualBox but not for Vendetta Online ...

---

### Post by Eclipticon on 2011-02-04
> **3Miro said:**
> Check to see if the compiz shortcut corresponds to a shortcut in the game. If so, change either one of them.

No, seems not to be the case ... but I might check with the developers if they are aware of any solution.

Great game, by they way ;-) [http://vendetta-online.com/](http://vendetta-online.com/)

---

