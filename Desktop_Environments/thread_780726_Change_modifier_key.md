---
title: "Change modifier key"
date: 2008-05-03
forum: Desktop Environments
---

### Post by Sutur on 2008-05-03
How do I change the modifier (move/scale) key from Alt, to Super?

---

### Post by Sutur on 2008-05-04
Bump.

---

### Post by mali2297 on 2008-05-04
Open the settings manager. For changing the modifier key used with the mouse, go to **Window Manager Tweaks -> Accessibility**. For changing other key bindings that relates to window management, go to **Window Manager -> Keyboard** and add a new theme.

---

### Post by Sutur on 2008-05-04
> **mali2297 said:**
> Open the settings manager. For changing the modifier key used with the mouse, go to **Window Manager Tweaks -> Accessibility**.

Thanks Martin, but I can't get there because compiz is managing tweaks.

---

### Post by mali2297 on 2008-05-04
> **Sutur said:**
> Thanks Martin, but I can't get there because compiz is managing tweaks.

Then you have to look in the configurations for Compiz. Install **compizconfig-settings-manager**, if you haven't got it already. 

I can't help you any further.

---

### Post by TheMemphisExperience on 2008-05-04
I'm sure the problem has been resolved, but in order to not leave this thread in cliffhanger mode...

in **compiz config settings manager**, hit the **move window** under the **uncategorized** section. It should be at the **bottom**.

The first item should be** initiate window move**. Change **alt + button 1** to **super + button 1**. Party.**_* HARD.*_**

---

### Post by Sutur on 2008-05-05
> **TheMemphisExperience said:**
> I'm sure the problem has been resolved, but in order to not leave this thread in cliffhanger mode...

in **compiz config settings manager**, hit the **move window** under the **uncategorized** section. It should be at the **bottom**.

The first item should be** initiate window move**. Change **alt + button 1** to **super + button 1**. Party.**_* HARD.*_**

I don't think compiz is actually what's managing it all. I think it's metacity. Alt+Right-Click brings up the metacity window menu (Minimize, Maximise, Always on Top, Close etc).

---

### Post by TheMemphisExperience on 2008-05-05
Are you using compiz-fusion?

If you are using Compiz-Fusion, then compiz is handling window behavior.

Alt+F2 should open a run application(this is true in GNOME, maybe not in XFCE). If it does not, open a terminal and input :

> ccsm

Regardless of whether you input the command into a terminal or the run application, this should open Compiz-Config Setting Manager. That is where you will find your white whale.

If you are the lone Ubuntu user not running Compiz-Fusion, I can't help you with an XFCE problem. But from the previous posts it sounds like you do have Compiz-Fusion. So...if you don't have Compiz...get it through the Synaptic Package Manager and join us.

---

### Post by Sutur on 2008-05-05
Ah, I found Resize plugin in compiz. Bindings are in there.

Thanking you all, marking solved.

---

