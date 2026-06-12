---
title: "Keyboard shortcuts in 8.04.1?"
date: 2008-07-22
forum: Desktop Environments
---

### Post by ardchoille42 on 2008-07-22
I found most of the keyboard shortcuts (Ubuntu 8.04.1) but can't seem to find one that I would like to memorize. When you right-click on a file you get the context menu. What is the keyboard shortcut for that? I've tried ALT+Enter, CTRL+ALT+Enter, SHIFT+ALT+Enter, and a few other but all they do is open the file instead of the file context menu. And I'm not sure how to set a custom keyboard shortcut for it because I don't know which command to use.

Any help?

---

### Post by Potatoj316 on 2008-07-22
Have you checked the keyboard shortcuts under System->Prefrences?  Also if your using a full keyboard (not a laptop keyboard) there is a context menu key, but I dont know if it works in Linux, I only ever use my laptop.

---

### Post by ardchoille42 on 2008-07-22
> **Potatoj316 said:**
> Have you checked the keyboard shortcuts under System->Prefrences?  Also if your using a full keyboard (not a laptop keyboard) there is a context menu key, but I dont know if it works in Linux, I only ever use my laptop.

Yeah, I checked the keyboard shortcuts under System->Prefrences, it isn't there. I have 11 computers and only one of the keyboards has that "context menu key", and it works like a charm.. no idea how to do it on the other 10 keyboards that don't have that special key, though.

---

### Post by pauper on 2008-07-23
This is an alternative to System--Preferences--Keyboard Shorcuts

```
gnome-keybinding-properties
```

If it's missing you should consider reinstalling gnome-control-center package.
"Keyboard Shorcuts" could be in the your menu list, but hidden at this time.
Make sure that the box is checked against its entry.

```
alacarte
```

Any other keybindings could be set here:

```
gconf-editor
```

Go to apps--metacity

You may check out "xbindkeys" package as well.

---

### Post by estyles on 2008-07-23
> **pauper said:**
> This is an alternative to System--Preferences--Keyboard Shorcuts

```
gnome-keybinding-properties
```

If it's missing you should consider reinstalling gnome-control-center package.
"Keyboard Shorcuts" could be in the your menu list, but hidden at this time.
Make sure that the box is checked against its entry.


I think he meant that the particular shortcut he was looking for wasn't in the keyboard shortcuts.  Not that Preferences->Keyboard Shortcuts wasn't there.  I could be wrong.

---

### Post by pauper on 2008-07-23
> I think he meant that the particular shortcut he was looking for wasn't
 in the keyboard shortcuts.

:oops: :oops: :oops:

You are probably better off looking through some nautilus glade files, such
as /usr/share/nautilus/ui/nautilus-directory-view-ui.xml
What keybinding is set in Nautilus' File--Properties? Do your Alt keys behave
normal with any other actions: Alt+F4, Alt+Home, Alt+Up ,etc.
Does Keyboard Preferences--Layout Options--Alt/Win key behavior is set to
anything other than Default?

By the way, if you want to customize context menu you should check out
nautilus-actions package:

```
sudo apt-get install nautilus-actions
```

Or get it from here:

[http://www.grumz.net/?q=taxonomy/term/2/9](http://www.grumz.net/?q=taxonomy/term/2/9)

---

### Post by ardchoille42 on 2008-07-23
> **estyles said:**
> I think he meant that the particular shortcut he was looking for wasn't in the keyboard shortcuts.  Not that Preferences->Keyboard Shortcuts wasn't there.  I could be wrong.

You are correct :)

---

### Post by BionicSeahorse on 2008-08-30
nvm :lolflag:

---

### Post by mimetist on 2009-01-04
I've found that the combination **Shift + F10** shows the context menu... but I don't know the command itself... and I think it would be very useful to change it for a better (and faster) keybind.

---

