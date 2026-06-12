---
title: "Enable Window Activate on Mouseover"
date: 2012-06-02
forum: Desktop Environments
---

### Post by ChaseEatsWorlds on 2012-06-02
I just installed 12.04 and I can't find out how to re-enable the setting on previous versions that would activate a window when you moved the mouse over it. It's a little thing but it really bugs me.

---

### Post by stinkeye on 2012-06-02
ccsm > general options > focus and raise behaviour
Unmark **click to focus**

---

### Post by fragos on 2012-06-03
That feature is in metacity which is still used, even with compiz running. Run the gconf-editer -- apps -- metacity -- general -- focus_mode. This is probably set to click. I recommend you set focus_mode to sloppy. Focus changes when the cursor enters a new window, you can move the cursor to the Desktop without changing focus.

---

### Post by stinkeye on 2012-06-03
> **fragos said:**
> That feature is in metacity which is still used, even with compiz running. Run the gconf-editer -- apps -- metacity -- general -- focus_mode. This is probably set to click. I recommend you set focus_mode to sloppy. Focus changes when the cursor enters a new window, you can move the cursor to the Desktop without changing focus.
Same thing really.
When you Unmark **click to focus** in ccsm
it changes the gconf setting to sloppy.

---

### Post by markbl on 2012-06-03
> **ChaseEatsWorlds said:**
> I just installed 12.04 and I can't find out how to re-enable the setting on previous versions that would activate a window when you moved the mouse over it. It's a little thing but it really bugs me.
But sloppy/mouse focus doesn't really work with Unity because you may select another window/app as cross over it to get to the global menu. I've preferred sloppy focus for many years but am reluctantly weaning myself off it now.

---

### Post by stinkeye on 2012-06-04
> **markbl said:**
> But sloppy/mouse focus doesn't really work with Unity because you may select another window/app as cross over it to get to the global menu. I've preferred sloppy focus for many years but am reluctantly weaning myself off it now.
Yeah, I've never used it but can see where it wouldn't work 
with the global menu.

---

### Post by fragos on 2012-06-04
Sloppy with the global menu isn't the best match but if you move the cursor through the desktop without touching another window to anywhere on the top panel Global menu will be what you want. One problem with focus by click is that if you open an application with a hot key, you still have to click that new window before you can do keyboard entry for it. Sloppy fixes that problem. IMHO global menu is a pain with a large screen and multiple windows open.

---

### Post by ChaseEatsWorlds on 2012-06-04
Thanks everyone! Got it all sorted out. I didn't have compiz installed. The global menu thing rarely effects me because if I need the menu for something I usually have it set to full screen.

---

