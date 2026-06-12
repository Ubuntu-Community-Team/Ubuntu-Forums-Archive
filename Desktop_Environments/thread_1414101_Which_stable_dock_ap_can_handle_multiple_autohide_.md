---
title: "Which stable dock ap can handle multiple autohide docks"
date: 2010-02-23
forum: Desktop Environments
---

### Post by Garnett on 2010-02-23
I want to replace all panels with three autohide docks.

Cairo-Dock seems slick but is temperamental. Specifically, when I set the docks to autohide and then hovered the mouse over the "recall" area, the dock "slid" onto screen and then back out indefinitely as long as the cursor was left there.

Also, it seems impossible to rename or delete newly created docks - which is a pretty fundamental flaw.

AWN can't do multiple docks which is a crying shame as it seems the most stable and reliable. I might have to use it in conjunction with a.n.other.

Docky seems good but again slightly temperamental.

Are there any others I could try?

---

### Post by fabounet on 2010-02-23
in Cairo-Dock, a dock is deleted as soon as there is no more icons inside.
also, you can rename them (although this is of poor interest) by renaming the .conf files in ~/.config/cairo-dock/current_theme (except the 'cairo-dock.conf' of course)

as for the bug with auto-hide, the fix is ready on the development version, and will be available in the next release.

---

### Post by Garnett on 2010-02-24
> **fabounet said:**
> in Cairo-Dock, a dock is deleted as soon as there is no more icons inside.
also, you can rename them (although this is of poor interest) by renaming the .conf files in ~/.config/cairo-dock/current_theme (except the 'cairo-dock.conf' of course)

as for the bug with auto-hide, the fix is ready on the development version, and will be available in the next release.Wow! Thanks for the awesome reply. That's damn comprehensive! Renaming the docks is useful (for an idiot like me) because I can name them Left, Bottom, and RIght, and not get confused when moving icons from one to another.

Can't wait for the next release.

---

### Post by fabounet on 2010-02-25
the 2.1.3-5 is released and should fix it ^^

---

