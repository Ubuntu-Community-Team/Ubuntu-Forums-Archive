---
title: "Workplace Switcher does not switch between screens"
date: 2011-09-26
forum: Desktop Environments
---

### Post by jameshedwards on 2011-09-26
i am running 11.04 on a Lenovo W520 Thinkpad. When I click on one of the 4 boxes in Workplace Switcher I don't switch to a new workplace.  I can right click on the apps window in the panel and select to move to another workspace and it will move the app, but I cannot click on the workplace switcher box corresponding to the workpace it moved to.

I appreciate any help given !

james

---

### Post by jameshedwards on 2011-09-27
I did not mention this is Ubuntu 11.04.

james

---

### Post by IWantFroyo on 2011-09-27
Are you using Unity? You have to hit enter.

Also. <ctrl><alt><arrowkey> works, too.

---

### Post by jameshedwards on 2011-09-27
> **IWantFroyo said:**
> Are you using Unity? You have to hit enter.

Also. <ctrl><alt><arrowkey> works, too.



Hitting enter does not change anything. ctl+alt, arrow keys does nothing. yes, I am running Unity.

james

---

### Post by IWantFroyo on 2011-09-27
I wasn't aware the panel switcher was in Unity. Then again, I haven't used Unity for a while.

Are you clicking the icon in the launcher? It will divide your screen into four smaller ones, where you can move windows, and click (and press Enter/Return) to go to that workspace.

---

### Post by jameshedwards on 2011-09-27
How can I tell if I am running Unity ?

JAMES

---

### Post by Frogs Hair on 2011-09-27
If you have a launcher on screen like that shown in the link you are running Unity . [http://design.canonical.com/2010/06/introduction-to-unity-launcher/](http://design.canonical.com/2010/06/introduction-to-unity-launcher/)

---

### Post by Copper Bezel on 2011-09-27
> Are you clicking the icon in the launcher? It will divide your screen into four smaller ones, where you can move windows, and click (and press Enter/Return) to go to that workspace.
You can just double-click the workspace. You can navigate it by keyboard, but you don't *have* to.

---

### Post by jameshedwards on 2011-09-27
> **Frogs Hair said:**
> If you have a launcher on screen like that shown in the link you are running Unity . [http://design.canonical.com/2010/06/introduction-to-unity-launcher/](http://design.canonical.com/2010/06/introduction-to-unity-launcher/)


I had that at first, but it went away. No clue on my part why it did. Now I have a panel top and bottom, apps minimize to the bottom panel. Thats cool, this layout is what I am used to.

So I right clicked on the bottom panel and selected "Add to Panel" and selected Workplace Switcher.

I did notice this:

```
root@je-thinkpad:/# ps ax | grep unity
 1606 ?        Sl     0:17 /usr/bin/unity-window-decorator

``` 

james

---

### Post by jameshedwards on 2011-09-27
> **Copper Bezel said:**
> You can just double-click the workspace. You can navigate it by keyboard, but you don't *have* to.


Neither work. Double click on workplace switcher does not do anything. ctl+alt+arrow keys does nothing.

james

---

### Post by Copper Bezel on 2011-09-27
Well, that applied to the Unity launcher's workspace icon, so. = (

For the main question, I'm not sure. If the Unity window decorator is being used, that means that you're using Compiz, and if Ctrl+Alt+Arrow doesn't work, that's a Compiz issue independent of the panel. In compizconfig-settings-manager, are the bindings for the Desktop Wall plugin configured?

---

### Post by jameshedwards on 2011-09-27
> **Copper Bezel said:**
> Well, that applied to the Unity launcher's workspace icon, so. = (

For the main question, I'm not sure. If the Unity window decorator is being used, that means that you're using Compiz, and if Ctrl+Alt+Arrow doesn't work, that's a Compiz issue independent of the panel. In compizconfig-settings-manager, are the bindings for the Desktop Wall plugin configured?


BINGO ! No they were not set and setting them made the Workplace Switcher work and ctrl+alt+arrow keys work. Thanks !!

james

---

### Post by Copper Bezel on 2011-09-27
Excellent! Just mark the thread as solved, Thread Tools in the upper right. = )

---

