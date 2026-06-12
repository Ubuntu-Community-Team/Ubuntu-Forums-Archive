---
title: "Make focus follow window-shifter Alt-tab under Compiz"
date: 2011-05-09
forum: Desktop Environments
---

### Post by cpbl on 2011-05-09
I upgraded to 11.04 and now the mouse focus doesn't change to the newly-selected window when I switch between windows with Alt-tab. 
Can you help me / point out where this is an option??

Thanks!

---

### Post by tastapod on 2011-05-26
I had the same problem. In Compiz Config Manager (sudo apt-get install compizconfig-manager), go to Static Application Switcher under Window Management.

Select the Appearance tab (which is weird - this should be on the behaviour tab), open the folded Selected Window Highlight section and check Focus on Switch.

I'm guessing this is an accidental fix - as you Alt-Tab through the windows the currently selected one gets focus, so it happens to retain the focus when you release the Alt key.

---

### Post by tastapod on 2011-05-26
> **tastapod said:**
> I had the same problem. In Compiz Config Manager (sudo apt-get install compizconfig-manager), go to Static Application Switcher under Window Management.

Select the Appearance tab (which is weird - this should be on the behaviour tab), open the folded Selected Window Highlight section and check Focus on Switch.

I'm guessing this is an accidental fix - as you Alt-Tab through the windows the currently selected one gets focus, so it happens to retain the focus when you release the Alt key.

Edit: it seems some windows are more "sticky" than others. If a gnome-terminal has focus and I switch windows, the original window retains focus. If I'm on firefox and I switch windows, the new window gets the focus (although the mouse arrow is still on the original window).

---

