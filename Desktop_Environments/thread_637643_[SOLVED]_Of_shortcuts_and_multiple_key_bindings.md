---
title: "[SOLVED] Of shortcuts and multiple key bindings"
date: 2007-12-11
forum: Desktop Environments
---

### Post by fdelosrios on 2007-12-11
Hi everybody, I have an unsolved issue in my Ubuntu desktop that prevents me from controlling smplayer from my remote. My remote is really an extension of my keyboard (no Irda), it generates some of the same scancodes my keyboard does and a couple of combo keystrokes (Ctrl+Shift+B and Ctrl+Shift+F is what RWD and FFW keys generate, any other acts like a single keypress). Well, I have it working for all my needs but for smplayer "Open file" dialog, an ordinary QT open file dialog. What I want to do is to control the "Go to parent folder" action of the dialog, any way is good for me if it works. My problem: "go to parent folder" action in QT is hardcoded (I think, at least I didn't find any way to change it) to Alt+Up shortcut and I need to trigger it with a single keystroke. I'm using a Gnome/Compiz fusion desktop and this is what I've already tried unsuccessfuly:
- I didn't find a way to map a single key to a combo with xmodmap or xkb, I think they're not supposed to do this.
- I use Gnome keyboard shorcuts and Compiz actions editor to map other keys to default actions or custom ones succesfully, but no trace about generating new keystrokes from others.
- Lineak and Keytouch weren't of any help on my quest.
- KDE khotkeys really rocks and it will fix my issue and will make my life easier. However, while being on a Gnome/Compiz desktop it won't work. I did several tests and it looks like no shortcut reachs it,  it's previously swallowed by Gnome keybindings. It's my guess and I hope I'm wrong. If you were wondering yes, khotkeys daemon is running.
- I changed shortcuts for Konqueror from the settings menu. It made no difference in the open file dialog window.
- I didn't bother to patch QT libraries to change this behaviour, I hope it will be an easier and less annoying solution.

Well, thank you for your time and I hope I'll manage soon to fix it.

Edited: my mistake to have missed the KDE keys config, I saw khotkeys but not keys module for kcmshell.

SOLUTION: you can change/add KDE/QT bindings from the KDE control panel keys module. Just exec "kcmshell keys" to get there.

---

