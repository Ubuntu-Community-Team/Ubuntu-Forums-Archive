---
title: "Gnome shortcut for tab switching?"
date: 2007-08-27
forum: Desktop Environments
---

### Post by Ryzol on 2007-08-27
I've noticed that if I have the mouse over the programs on the taskbar or the tabs of conversation windows in pidgim(gaim) that using the scrollwheel will cycle through those tabs and programs. Is there a keyboard shortcut for this? I can't find this documented in the gnome user's guide.

---

### Post by Wolki on 2007-08-27
> **Ryzol said:**
> I've noticed that if I have the mouse over the programs on the taskbar or the tabs of conversation windows in pidgim(gaim) that using the scrollwheel will cycle through those tabs and programs. Is there a keyboard shortcut for this? I can't find this documented in the gnome user's guide.

The official shortcut that should work in every gnome application is ctrl-alt-pageup for previous tab and ctrl-alt-pagedown for next tab. In most applications, ctrl-pageup and ctrl-pagedown will also work, some widgets, like the editor thing in gedit, have already other actions on the ctrl-page(up/down) shortcut so you'll need the full variant there. In applications that support reordering tabs (should be most), holding shift while switching tabs will move the tab in that direction instead of switching.

Note that gnome applications usually do not cycle (ie go from last back to first) but only go into the specified direction. This is iirc for accessibility reasons, and it's generally nice to have a natural stopper once you're used to it - you don't need to count the tabs to move from anywhere to the first or last tab, and can be less accurate with the keyboard shortcuts or mousewheel. 

This may or may not apply to applications that are not part of gnome like firefox or gaim/pidgin, which may use slightly or largely different tab behaviors.

---

### Post by Ryzol on 2007-08-27
Thanks that saved a lot of frustration! :D

---

### Post by jim_p on 2007-08-28
I use Ctrl+Tab for most tab-related apps and it works fine.
Its like "Alt+tab to cycle through apps (windows), and Ctrl+Tab to cycle through each window's tabs"

---

### Post by Wolki on 2007-08-28
> **jim_p said:**
> I use Ctrl+Tab for most tab-related apps and it works fine.
Its like "Alt+tab to cycle through apps (windows), and Ctrl+Tab to cycle through each window's tabs"

Then you're not using many gnome apps with tabs. Ctrl-tab will not work in them, as that keybinding is bound to "move focus to the next widget", like normal tab. You need both as  some widgets need to be able to swallow the tab key (like the text editing area in gedit, which uses the tab key to insert tab characters), so you need another binding for these cases or you'll have areas of the application that you can't navigate with the keyboard, which is both an accessibility no-no and annyoing to users that prefer using the keyboard.

---

### Post by djrobthaman on 2008-07-16
In my never ending search for easy tab navigation I found this post.  Based on the above info, or otherwise, anybody know how to change the default gnome next tab / prev tab shortcut (or at least the gedit shortcut) to "ctrl + tab" instead of "ctrl+alt+page up/down"

Thanks a bunch

---

