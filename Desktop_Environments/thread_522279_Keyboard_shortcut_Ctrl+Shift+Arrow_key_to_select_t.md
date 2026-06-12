---
title: "Keyboard shortcut Ctrl+Shift+Arrow key to select text"
date: 2007-08-10
forum: Desktop Environments
---

### Post by praet on 2007-08-10
Keyboard shortcut Ctrl+Shift+Arrow key to select text doesnt seem to work properly.

I am using ubuntu 7.04, Xgl, compiz and all is running happily. The problem happens while editing in any text box.  Shift + arrows select that character, Ctrl + arrows move the cursor by one word, BUT both together do not move the cursor or select anything (no effect).  That key combination should select the entire word.  Shift + Home as well as Shift + End, work as expected. 

It is a strange issue but it would be useful to know how to check for proper key configs.  I get the correct result in a regular non-Xgl gnome  session.


Thanks for any help.

.praet

---

### Post by praet on 2007-08-15
Ok I have narrowed this issue to a single compiz-fusion plugin, ezoom.
Disabling the Enhanced Zoom Desktop Plugin corrects the combination key action.
I will research it a bit more and report it to the plugin author if necessary. 

If anyone can verify this issue your comments are welcome.

---

### Post by sc00ter on 2007-08-16
Hi,

I also have this problem when the Enhanced Zoom Desktop plugin is active. I'm running Feisty 7.04 and Compiz Fusion (from the Trevino repository)

---

### Post by KhaaL on 2007-08-16
If you go into the ezoom plugin in CCSM, go into actions and reassign the keyboard shortcuts from there. 

You can also do this directly in your compiz settings ini file :)

---

### Post by praet on 2007-08-16
Thanks for your post KhaaL, I did look at the keybindings at first but seem to have overlooked that in fact there *are* keybindings that interfere with text input.  

Pan Zoom Left is set to Shift+Ctrl+Left
Pan Zoom Right is set to Shift+Ctrl+Right
Pan Zoom Up is set to Shift+Ctrl+Up
Pan Zoom Down is set to Shift+Ctrl+Down

I suppose these should only be active if ezoom is in a zoomed in state.  Otherwise changing them away is easy enough.

Thanks.

---

