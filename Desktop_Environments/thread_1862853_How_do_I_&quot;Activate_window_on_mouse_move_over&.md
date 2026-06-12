---
title: "How do I &quot;Activate window on mouse move over&quot;?"
date: 2011-10-17
forum: Desktop Environments
---

### Post by ked on 2011-10-17
Can't find this option in Unity... Am I blind?

Ked...

---

### Post by ked on 2011-10-17
It can't be only me missing this option??? Selecting a window without having to click it??? Come on...

---

### Post by mcduck on 2011-10-17
Install the [gnome-tweak-tool]("apt:gnome-tweak-tool"), the option appears in the Window section.

I don't think there's any configuration option for this available by default.

---

### Post by stinkeye on 2011-10-17
For compiz
ccsm > general options > focus and raise behaviour
Disable **click to focus** and adjust the **auto-raise delay** if needed.
Can be hard to use if set too short.

---

### Post by ked on 2011-10-17
> **stinkeye said:**
> For compiz
ccsm > general options > focus and raise behaviour
Disable **click to focus** and adjust the **auto-raise delay** if needed.
Can be hard to use if set too short.

EXACTLY what I wanted :)

Tanx!

---

### Post by cogcog on 2011-10-22
Did you find that this works for you long term? It fixes the problem for me for one login session, but next time I log in, it has reverted back to the behavior where you have to click on windows before they get focus.

---

### Post by markbl on 2011-10-22
> **ked said:**
> EXACTLY what I wanted :)

Are you sure you want that?

I have always preferred "focus follows mouse" also but it doesn't really work on unity due to global menus (because the menu will/may change as you move your mouse over another app's window to get to the panel bar).

---

### Post by cogcog on 2011-10-23
> **markbl said:**
> Are you sure you want that?

I have always preferred "focus follows mouse" also but it doesn't really work on unity due to global menus (because the menu will/may change as you move your mouse over another app's window to get to the panel bar).

Yeah, the global menu bar really screws with this! But luckily you can turn it off. I never really understood click-to-focus (why is it useful to send mouse movements to a window that you aren't interacting with..?) But I also don't see the advantage of a global menu (why would you visually and spatially separate part of an application from the rest?) So for me, the obvious best setting is menus-in-windows with focus-follows-pointer.

---

### Post by ked on 2011-10-23
> **cogcog said:**
> Did you find that this works for you long term? It fixes the problem for me for one login session, but next time I log in, it has reverted back to the behavior where you have to click on windows before they get focus.

I'm not sure as I rarely log out, but I'll look into it tomorrow at work.

---

### Post by ked on 2011-10-23
> **markbl said:**
> Are you sure you want that?

I have always preferred "focus follows mouse" also but it doesn't really work on unity due to global menus (because the menu will/may change as you move your mouse over another app's window to get to the panel bar).

Well, I removed the global menu - guess it was the first thing I did along with removing the overlay scrollbar...;)

---

### Post by ked on 2011-10-24
> **cogcog said:**
> Did you find that this works for you long term? It fixes the problem for me for one login session, but next time I log in, it has reverted back to the behavior where you have to click on windows before they get focus.

For me the settings stays put, also after reboot. Now, I only want to change the scrollbar color... it's really annoying not finding out about it...](*,)

---

### Post by mc4man on 2011-10-24
> **ked said:**
> For me the settings stays put, also after reboot. Now, I only want to change the scrollbar color... it's really annoying not finding out about it...](*,)
For the overlay-scrollbar - 
I change that here for ambiance in /usr/share/themes/Ambiance/gtk-3.0/settings.ini
& also  in  /usr/share/themes/Ambiance/gtk-2.0/gtkrc
(in 11.04 I may have also edited  ..gtk-3.0/gtk.css

The scrollbar is changed in the gtk-3.0/settings.ini thru the 
nselected_bg_color:#f07746
#f07746 is that orange color
More than just the scrollbar is changed, it affects pretty much all that was orange before.
The same in the gtkrc changes highlighting in firefox, maybe elsewhere

May be other ways, myself want to kill the orange everywhere

---

