---
title: "anchor desktop switcher in Xfce 4.10?"
date: 2013-10-10
forum: Desktop Environments
---

### Post by Buntu Bunny on 2013-10-10
I've been trying to figure out how to anchor desktop switcher in Xfce 4.10. It seems attached to the left, but moves to accommodate open windows in each particular workspace. I use 4 workspaces daily, to keep related parts of projects in their own workspace. Switching between work spaces is slowed down because of this, as I try to visually locate each on the switcher. Plus, it makes me somewhat sea sick! 

There's nothing on this in the Xfce documentation, and no one else seems to be discussing it as a problem. Is it possible to anchor workspace switcher to the right of the top panel, like it is in Xfce 4.8?

---

### Post by Toz on 2013-10-10
If I understand correctly....

Right-click the panel, select Panel->Panel Preferences and go to the Items tab. on this tab, you an move around the items that are present on the panel. If not already therem try moving the "Window Buttons" plugin to the bottom of the list (will appear on the far right of the panel). If it still moves around, you may need to add an Expanding Separator just before it to force it to the right.

[[img]http://en.zimagez.com/avatar/ss189.png[/img]]("[url=http://en.zimagez.com/zimage/ss189.php)"][[img]http://en.zimagez.com/avatar/ss189.png[/img]](http://en.zimagez.com/zimage/ss189.php)[/URL]

---

### Post by Buntu Bunny on 2013-10-10
Toz, that helped tremendously, thank you. The switcher remains stationary toward the left of the panel. I'm used to it in the far right-hand side (Xfce 4.8), but I can live with this. Before asking here, I tried putting in some separators, but AFAIK, none expand. Is that a special type of separator?

---

### Post by slickymaster on 2013-10-10
That's strange, I can move the "Workspace Switcher" to any place I want in the panel. In my case I have "Windows Buttons" on top of the list, but I'm not convinced that it could be related.

---

### Post by Toz on 2013-10-10
> **Buntu Bunny said:**
> ...I tried putting in some separators, but AFAIK, none expand. Is that a special type of separator?
If you double-click the separator item, a dialog will popup that will allow you to set the expand property (checkbox).

---

### Post by Buntu Bunny on 2013-10-10
> **slickymaster said:**
> That's strange, I can move the "Workspace Switcher" to any place I want in the panel. In my case I have "Windows Buttons" on top of the list, but I'm not convinced that it could be related.

slickymaster, are you saying that your workplace switcher stays put? When "windows buttons" was higher on the list, everything below it would shift on the panel to accommodate the number of windows I had open. With  "windows buttons"  on the bottom of the list, everything else stays put. What I have now is in a screenshot below.

> **Toz said:**
> If you double-click the separator item, a dialog will popup that will allow you to set the expand property (checkbox).

Toz, I didn't know that. Thank you. I'll have to play around and see what I can do.

---

### Post by slickymaster on 2013-10-10
> **Buntu Bunny said:**
> slickymaster, are you saying that your workplace switcher stays put? When "windows buttons" was higher on the list, everything below it would shift on the panel to accommodate the number of windows I had open. With  "windows buttons"  on the bottom of the list, everything else stays put. What I have now is in a screenshot below.
...
Yes, that's what I'm saying. Right now I have ten different windows open and minimized but everything else stays put.[ATTACH=CONFIG]246860[/ATTACH]

---

### Post by Dennis N on 2013-10-10
Just for fun, the window buttons can even be centered by using expanded separators before and after the window buttons item. The buttons stay centered as more are opened. The stuff to the right doesn't move around either.

---

### Post by Buntu Bunny on 2013-10-10
@ slickymaster, attached is an image of how my workspace switcher was moving along the panel, depending on which workspace I was using. Moving the windows button did help. Other than that, I'm not sure what's going on (my Linux knowledge isn't great enough for me to distinguish between a bug and operator error, LOL) You will recall that I updated from Xfce 4.8 on Ubuntu 12.04, but I'm not sure if that's relevant.

---

### Post by Buntu Bunny on 2013-10-10
> **Dennis N said:**
> Just for fun, the window buttons can even be centered by using expanded separators before and after the window buttons item. The buttons stay centered as more are opened. The stuff to the right doesn't move around either.

Well, that works too. In fact, it forced workplace switcher to the right, like it was in for me in Xfce 4.8.  Thanks Dennis N!

---

### Post by Dennis N on 2013-10-10
You need an expanded separator between the window button list and the clock, That will fix it. 
With 4.8 I don't think you needed to do that.

---

### Post by Buntu Bunny on 2013-10-10
> **Dennis N said:**
> You need an expanded separator between the window button list and the clock, That will fix it. 
With 4.8 I don't think you needed to do that.

Well, it worked and things are the way I like them. :p

Thank you to Dennis N, slickymaster, and Toz! The help was greatly appreciated and I'm a happy camper once again.

---

### Post by Dennis N on 2013-10-10
Glad that's fixed for you. Must have been annoying having the items on the right shift back and forth.

---

### Post by Buntu Bunny on 2013-10-10
Yes, but now I'm used to scanning the panel for it, LOL. It's amazing what we can get used to, but I do like it back in it's "old"place.

---

