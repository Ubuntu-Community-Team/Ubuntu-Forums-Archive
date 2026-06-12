---
title: "Disable &quot;Select to copy&quot; and &quot;Middle button Paste&quot; How to?"
date: 2011-08-28
forum: Desktop Environments
---

### Post by tomhc on 2011-08-28
How would one disable "Select to copy" and "Middle button Paste". Form forums i read, you can disable "Middle button Paste" by editing a "Xorg Config file", does anyone know of a alternative way? Editing the "Xorg" file does not remove the select to copy function. I would  really like to remove it. :popcorn: :), but can not find a forum or article that helps with this. :( 


So i would like to know how to disable "Select to copy" and "Middle button Paste". I am running KDE in kubuntu 11.04. 



As a side note: Why...
I would like to disable select to copy becuase:
I highlight text sometimes to see it better and to know where i left off when reading articles while switching tabs. I would like to not have something i selected to appear in a social messaging application. 

And I would like to use the middle button to close applactions, or open hyperlinks Via Middle Button, (as middle button opens them in a inactive new tab {Which is very useful}).



Please don't say "Get used to it" or "Select to copy is the BEST, MOST AWESOME, feature in Linux. Why would you want to remove it"


If you don't have time, Please just tell me if this is possible, so that i can continue searching. :)

:KS Thank you ahead of time Linux Angels! :P

---

### Post by Toz on 2011-09-05
Have a look at: [https://wiki.ubuntu.com/X/Config/Input#Example:_Disabling_middle-mouse_button_paste_on_a_scrollwheel_mouse]("https://wiki.ubuntu.com/X/Config/Input#Example:_Disabling_middle-mouse_button_paste_on_a_scrollwheel_mouse")

---

### Post by tfkm on 2013-01-18
> **Toz said:**
> Have a look at: [https://wiki.ubuntu.com/X/Config/Input#Example:_Disabling_middle-mouse_button_paste_on_a_scrollwheel_mouse](https://wiki.ubuntu.com/X/Config/Input#Example:_Disabling_middle-mouse_button_paste_on_a_scrollwheel_mouse)
A completely useless answer/howto. Rather than disabling the paste action, it disables the entire middle mouse button. (And would thus render middle-click in Firefox to open a link in a new tab window useless, for example.)

---

### Post by mcduck on 2013-01-18
Sorry to tell you, but there's not going to be any easy way to accomplish what you want.

You could follow this guide and try to adopt it to apply to current GTK2 and GTK3 versions, and perhaps find out if you can find a way to do similar thing with other toolkits (like Qt) if you have any applications using them: [https://www.assembla.com/spaces/slipstream/wiki/Disabling_GTK%27s_middle_mouse_button_functionality]("https://www.assembla.com/spaces/slipstream/wiki/Disabling_GTK%27s_middle_mouse_button_functionality")

Other than that, the feature is called "primary selection", and it's part of the X Window's selection standard. If nothing else, knowing the correct name should help in your search... ;)

---

### Post by Elfy on 2013-01-18
Old thread closed.

---

