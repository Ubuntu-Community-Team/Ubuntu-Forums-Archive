---
title: "Window animation (compiz), how to &quot;grab&quot; pull-down menu window info"
date: 2010-05-13
forum: Desktop Environments
---

### Post by paxxus on 2010-05-13
Hi,

Some of my applications use different window types for pull-down menus than what compiz window animation think. This means that I get normal open window animation on these pull-down menus instead of the menu-theme.

Inside the CompizConfig you can specify exactly which window types the different animations apply to, and you can use "grab" to probe your window for this info.

My problem is that I can't "grab" the info for the pull-down, since it leaves "grab" mode once I try to open the menu (and grabs the info for the parent window instead of the menu).

How do I get to know the window properties of the pull-downs, so that I can map them to the relevant window animation theme?

---

### Post by paxxus on 2010-05-13
anybody?

---

### Post by paxxus on 2010-05-14
Even though xwininfo doesn't seem to give me the same informations as the CompizConfig window grab tool, I tried this:

sleep 5 && xwininfo -all

This gives me 5 secs to pull down the menu before the grabber starts. But alas, it won't grab while a pull-down is active:

```
xwininfo: Please select the window about which you
          would like information by clicking the
          mouse in that window.
xwininfo: error: Can't grab the mouse.
```


I have now been forced to disable window open/close animation because of the menu problem.

I'd still really like some suggestions how to fix this. I have two often used applications, where compiz thinks the pull-downs are normal windows. Surely others have run into (and solved?) this problem :confused:

---

### Post by mcduck on 2010-05-14
If it helps anyhting, the only window classes I've seen for menus are "Menu", "DropdownMenu" and "PopupMenu".

For example I use "(class=Menu|PopupMenu|DropdownMenu)" as selector in the Opacity plugin to make all my menus transparent. I'm yet to see an application that wouldn't get transparent menus this way.

(If that still doesn't do the trick then make sure you have the "Workarounds"-plugin enabled, and check if there's a window type fix for the application you are having problems with..)

---

### Post by paxxus on 2010-05-14
"Workarounds" is enabled.

I have "(type=Menu | PopupMenu | DropdownMenu | Dialog | ModalDialog | Normal)" to match menus.

Extremely frustrating that I can't get the window info for the pull-down.

I have the problems with a Citrix client and a Tcl/Tk based application.

---

### Post by paxxus on 2010-05-16
mcduck, I now see that I misread your reply. You talk about the class variable whereas the default setting seem to only use the type variable.

Using your mtach code I can indeed match the menus, I use wildcards like (class=Menu* | class=*Menu) just to be on the safe side.

Unfortunately this only solved the problem for one of my two problematic applications, the citrix client still has the problem.

I realized that I could use the wildcard expression to determine the window class, starting with class=a*, class=b*, and so on until I get a match, and then move on to the next letter. But I don't have the energy for that right now ;)

---

