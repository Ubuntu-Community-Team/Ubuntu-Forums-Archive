---
title: "alt+tab problems with compiz fusion"
date: 2007-07-02
forum: Desktop Effects &amp; Customization
---

### Post by TimmyJ on 2007-07-02
Hey, I have a weird problem with my alt+tab behavior in compiz fusion (from trevinos repo). When going through my windows with alt+tab it scrolls through the window by 2, so I can only select every other window using alt+tab. I looked through the configuration and didn't find anything that would suggest this kind of behavior. I should also note that my super+tab effect (selecting windows in a big ring) works fine though. Anyone else have this problem/know how I can fix it?

---

### Post by Jexel on 2007-07-02
I'm currently under Vista so i can't check for you but it's to do with the window switching functionality. In the shortcuts menu you should see two copies of "alt-tab", one of it should be "control+alt+tab". So just change it and alt tab should be working fine :) But be aware that one of the altab is for the current viewpoint and the other altab is for all viewpoints.

---

### Post by inckie on 2007-07-02
Indeed.

The first pair is for windows on the current viewport; the second, for all open windows; and the third, for the windows in the currently selected window group.

BTW, the Ring Switcher plugin has the three "next/previous window" pairs properly named with properly set shortcuts. Why they left the Application Switcher plugin that way is beyond me.

---

### Post by mottalli on 2007-07-02
Hi,
The same thing is happening to me, ALT+TAB jumps two windows ahead. However, ALT+SHIFT+TAB jumps only one window below (the expected behavior).
However, this is only happening on one of my computers. I have a laptop and a desktop computer, both are using Ubuntu 7.04 i386, my desktop computer is having this problem while my laptop isn't.

Anyone else has seen this?

---

### Post by ivesjd on 2007-07-02
I think I solved it by removing the alt-tab keyboard shortcut in Ubuntu. Still works because of Compiz Fusion.

---

### Post by jackmc on 2007-07-10
> **mottalli said:**
> Hi,
The same thing is happening to me, ALT+TAB jumps two windows ahead. However, ALT+SHIFT+TAB jumps only one window below (the expected behavior).
However, this is only happening on one of my computers. I have a laptop and a desktop computer, both are using Ubuntu 7.04 i386, my desktop computer is having this problem while my laptop isn't.

Anyone else has seen this?

I have the exact same issue... Any solution yet?

EDIT: I have two keybindings set to alt tab (as mentioned in a previous post) but they wont change :(

EDIT2: I have disabled the first two keybindings, now it works fine :)

---

### Post by chadlongstaff on 2007-07-11
This thread isn't very helpful so far, I've found my solution to the problem is to ignore the compiz-fusion settings instead go to system>preferences>keyboard shortcuts then remove the key binding of alt-and-tab from "Move between windows with popup" (double click on the key-binding then backspace to disable). Shouldn't even be any need to restart compiz-fusion.

---

### Post by orbital on 2007-07-14
Disabling alt-tab shortcut from Ubuntu - preferences - keyboard shortcuts solved the problem for me.

---

### Post by Legend1222 on 2007-08-11
I don't recommend modifying your ubuntu keyboard preferences, because if you ever have to fall back to metacity from compiz, I believe you will loose your alt-tab functionality. 

The problem comes from a misconfiguration in Compiz. Go into CompizConfig Settings Manager, under application switcher, and you will see in there that alt-tab is assigned to both "Next Window" and "Next Window (All Windows)". Either reassign "Next Window (All Windows)" to something else, or just disable it. Then everything will work as expected.

---

### Post by thebigham on 2007-08-11
> **Legend1222 said:**
> I don't recommend modifying your ubuntu keyboard preferences, because if you ever have to fall back to metacity from compiz, I believe you will loose your alt-tab functionality. 

The problem comes from a misconfiguration in Compiz. Go into CompizConfig Settings Manager, under application switcher, and you will see in there that alt-tab is assigned to both "Next Window" and "Next Window (All Windows)". Either reassign "Next Window (All Windows)" to something else, or just disable it. Then everything will work as expected.

Nope, that didnt worked for me. I changed the Ubuntu shortcut key to something else, and it worked. Pressing that ubuntu shortcut key that i changed worked, and Alt+tab from compiz also worked. :)

---

### Post by wate on 2007-09-27
> **Legend1222 said:**
> I don't recommend modifying your ubuntu keyboard preferences, because if you ever have to fall back to metacity from compiz, I believe you will loose your alt-tab functionality. 

The problem comes from a misconfiguration in Compiz. Go into CompizConfig Settings Manager, under application switcher, and you will see in there that alt-tab is assigned to both "Next Window" and "Next Window (All Windows)". Either reassign "Next Window (All Windows)" to something else, or just disable it. Then everything will work as expected.

Ty Legend,
 I was  assuming this is a compiz bug or even nvidia driver conflict, so I was on the way reinstalling new-old drivers and probably I would mess up a bit  and make compiz crash more often... leading this to installing fresh copy of Ubuntu :)

Thank You for saving me some stress and for keeping my OS more clean :)

---

### Post by PPPP on 2007-11-27
Sorry to bring this back to life.  

I have a similar problem but not quite the same.  Instead of jumping by 2, sometimes, it just keeps scrolling as if the keys were stuck.  It doesn't happen everytime but may be once an hour?  I have reassigned "Next window (All windows)" and "Prev window (All windows)" to Ctrl+8 & Ctrl+7 respectively.  

Any idea?

---

