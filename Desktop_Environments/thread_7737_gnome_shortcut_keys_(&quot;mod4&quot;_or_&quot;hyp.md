---
title: "gnome shortcut keys (&quot;mod4&quot; or &quot;hyper&quot;)"
date: 2004-12-10
forum: Desktop Environments
---

### Post by burlap on 2004-12-10
When using fluxbox and windowmaker I got used to using "windows" ("hyper", "super" or whatever the name of this key with windows logo is) key instead of "alt" (as it is more useful in other apps). This time I would like to use Gnome for a while, but...

Here is the problem: 
It is impossible to set "hyper" (mod4) through desktop preferences (Keyboard shortcuts) as it captures one key only (calling it "Super_L") with no combination (i.e. I press mod4+ctrl+a to be my shortcut and all I get is "Super_L"). 

So I set everything with the Configuration Manager (it uses "mod4", just like other wm). And I have almost everything working - except for switch_windows key (alt+tab). Mod4+Tab just shows the switching panel but does not switch windows. Is it a bug or have I missed something?

---

### Post by ketilkn on 2004-12-16
I am not sure if I understand you correctly. Have you gotten the "Windows key" to work as mod4 or not?

If "windows key" behave as Super_L:

Go into the computer menu -> desktop preferences -> keyboard. There is a tab called something like "Alternative layout" (I use norwegian). Its the third tab from the left. There you will find alt/hyper behaviour. Select Hyper is mapped to win-keys. Click Add.

Thats it. "Windows key" now behave as mod4.

Does this answer your question?

---

### Post by burlap on 2004-12-16
I did not know about this possibility to map "hyper" through keyboard preferences, that is why I was unclear. 

I haved tried this, but this does not really matter or solve the problem except for the fact, that now I can bind keyboard shortcuts to "mod4" through gnome-keybinding-properties (before it was possible only with configuration manager). 

Once again - to sum up.

I have windows key set to "hyper as alt keys" in gnome-keyboard-properties. 
I can bind it (as "mod4") with shortcuts via gnome-keybinding-properties.  
Option "Move between windows with popup" does not work whatever combination with "mod4" I set there. The only thing I get is popup. No moving windows.

---

### Post by ketilkn on 2004-12-17
That is odd. I do not have the problem.

Perhapse the switch immediatly option works?

---

### Post by burlap on 2004-12-18
I know it's odd, "switch immediately" works (I like popup more, especially with spatial nautilus). Other shortcuts also work (I use mod4 for "switch to desktop" and different "maximize/minimize window" options).

---

### Post by Gianni Exile on 2005-04-29
[QUOTE=ketilkn]I am not sure if I understand you correctly. Have you gotten the "Windows key" to work as mod4 or not?

If "windows key" behave as Super_L:

Go into the computer menu -> desktop preferences -> keyboard. There is a tab called something like "Alternative layout" (I use norwegian). Its the third tab from the left. There you will find alt/hyper behaviour. Select Hyper is mapped to win-keys. Click Add.

Thats it. "Windows key" now behave as mod4.

Does this answer your question?[/QUOTE]

This works perfectly... THANKS!!
I had some Xmodmap cruft which works, but is annoying to have to copy around... much simpler to do as proposed here.

---

### Post by liuter2045 on 2007-05-15
Re: gnome shortcut keys (&quot;mod4&quot; or &quot;hyper&quot;)
<snip>

---

### Post by gingasha927 on 2007-05-15
> **ketilkn said:**
> I am not sure if I understand you correctly. Have you gotten the &quot;Windows key&quot; to work as mod4 or not?

If &quot;windows key&quot; behave as Super_L:

Go into the computer menu -&gt; desktop preferences -&gt; keyboard. There is a tab called something like &quot;Alternative layout&quot; (I use norwegian). Its the third tab from the left. There you will find alt/hyper behaviour. Select Hyper is mapped to win-keys. Click Add.

Thats it. &quot;Windows key&quot; now behave as mod4.

Does this answer your question?


<snip>

---

### Post by quagz1 on 2007-11-03
Worked a treat for me!!

---

