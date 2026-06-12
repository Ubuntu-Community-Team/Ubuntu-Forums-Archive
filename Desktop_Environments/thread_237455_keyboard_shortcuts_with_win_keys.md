---
title: "keyboard shortcuts with win keys"
date: 2006-08-16
forum: Desktop Environments
---

### Post by zheek on 2006-08-16
Hi guys,

While working with ms windows, I've become quite used to keyboard shortcuts using (a combination of) the win key (that special key located between ctrl and alt)

In particular I am most fond of the following:
win   => shows the start menu
win+d => shows the desktop
win+e => starts explorer

So I would naturally like to have the following in Ubuntu:
win   => shows the Gnome start menu
win+d => shows the desktop
win+e => starts Nautilus

However, long as I tried with the keyboard layout manager and key shortcut tool. I've not been able to get it perfectly right.

The problem is,  I can either set the win key as a shortcut key or as a combination key for a shortcut, but not together.
So, when the win+d and win+e shortcuts are correctly set, the win shortcut doesn't work. If win works, win+d and win+e shortcuts don't.

Anyone able to get all 3 shortcuts to work together?

Any help or pointers would be greatly appreciated.

---

### Post by aysiu on 2006-08-16
> **zheek said:**
> 
The problem is,  I can either set the win key as a shortcut key or as a combination key for a shortcut, but not together. Sorry, but that's the way it is.

---

### Post by zheek on 2006-08-17
Ok,

It was a nice to have anyway.
At least I know not to bother with it anymore.

Thanks

---

### Post by andiii on 2006-09-05
edit: <  problem solved.... amaroK had taken the shortcut.. >

I have a group of shortcuts that stopped working suddenly.

With Win+1(2,3,4) I could move a window to Desktop 1,2,3,4. Doesn't work anymore. The Shortcut is set when I look at Administration-Keyboard Shortcuts..

It's not that the windows key doesn't work at all, because Win+Cursor to switch workspaces is still good. I installed new amaroK version and some other things, but I can't really imagine why this would break my sweet shortcuts.

edit: win+q(w,e,r) works..
So something is wrong with my Num-Keys. (I only have the row above the letters on my laptop). Pressing Num LK to make this yellow LED glow didn't make it work.

---

### Post by vloris on 2006-11-10
> **aysiu said:**
> Sorry, but that's the way it is.

No, it's not.
By default the windows-key is just that: a windows key. It functions like the normal keys. The behaviour you want is to let it function as a modifier key, like Ctrl, Alt, Shift.

You can accomplish that in System->Preferences->Keyboard, Layout Options
Here you have a setting "Alt/Win key behaviour", I had to select "Super is mapped to the Win-keys" to be able to create shortcuts like win+d.

I know, there is a word "default" after that setting, but nevertheless, I had to set it explicitly.

---

### Post by aysiu on 2006-11-10
> **vloris said:**
> No, it's not.
By default the windows-key is just that: a windows key. It functions like the normal keys. The behaviour you want is to let it function as a modifier key, like Ctrl, Alt, Shift.

You can accomplish that in System->Preferences->Keyboard, Layout Options
Here you have a setting "Alt/Win key behaviour", I had to select "Super is mapped to the Win-keys" to be able to create shortcuts like win+d.

I know, there is a word "default" after that setting, but nevertheless, I had to set it explicitly.
The OP wanted it to be **both** its own key **and** a modifier key.

You're saying it can be a modifier key. I know that. I'm saying it can't be both. It's either own key or a modifier key.

Read before you say "No, it's not."

---

