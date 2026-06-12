---
title: "Super key/Windows key as modifier AND standalone"
date: 2007-10-30
forum: Desktop Effects &amp; Customization
---

### Post by SDraconis on 2007-10-30
I'm trying to get my Windows-like shortcut keys working in Ubuntu, and having a bit of trouble.  In short, I want to get the left Super key to open up the panel menu, and at the same time act as a modifier for other combinations (super + L for locking, super + t for terminal).  Unfortunately the keyboard settings only seem to let me have it one way or another.  I even tried using defaults, setting panel to Super_L, and then changing settings and getting mod4 + T to be terminal, but the former binding seems to take precedence.  It would also be nice if the panel menu popped up on the *release* of the Super key rather than keydown.

I know this isn't a Linux/X thing, as I got these shortcuts working in IceWM back when I used Gentoo.  I'm guessing it's a Gnome issue.  Anybody got a fix?

---

### Post by schnaburelis on 2007-10-30
Hi

I had exactly the same problem.

Just open the Gnome Editor (gconf-editor) and navigate to apps->metacity->global_keybindings. Here you can set the bindings manually

i.e. to set the run dialog to [windows]+[r] edit the key panel_run_dialog to <Super>r

---

### Post by SDraconis on 2007-10-30
Thanks, but this still only got me one of the behaviors.  I set panel_run_dialog to <Super>r, which worked fine.  I then tried setting panel_main_menu to just <Super> and that did not work.  If I set panel_main_menu to Super_L, the panel menu works, but then Super+r for run dialog doesn't.  How do I get both of these behaviors to work concurrently?

EDIT: It appears this is actually a problem with the panel menu.  No shortcut keys work while the panel menu is open.  My issue could also be fixed if the panel menu could open on keyup rather than keydown.  Also, I'd like to make the same button both open the panel menu and close it (toggle).  Any ideas?

---

