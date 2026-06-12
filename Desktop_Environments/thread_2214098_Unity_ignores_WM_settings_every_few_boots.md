---
title: "Unity ignores WM settings every few boots"
date: 2014-03-30
forum: Desktop Environments
---

### Post by NickLanam on 2014-03-30
Hello,

In the last week, whenever Unity starts up, it will occasionally ignore most of my window manager settings.

These include custom keybindings (be they through Unity or Compiz). This includes my choice to clear most of the Ctrl+Alt keybindings - there is a separate and possibly related issue where, if any of those are enabled, Ctrl+Alt triggers the first non-compiz binding with those two keys in it, before I press the other key - and the first binding happens to be minimize. The latter issue happens even on a completely fresh installation of Ubuntu on this computer, but not my laptop.

Unity's own various settings windows, the Unity Tweak tool, and CCSM all show that my settings have not been forgotten, but they are all behaving as though the defaults were used instead. Each setting that I manually set to the already stored value again is honored immediately, but I would much rather NOT script a long chain of gconftool2 and compiz settings.

As far as I am aware, the only thing that has changed other than routine updates is that I installed Terminator.

I do not know which logs to peruse for this issue, but if I can find them I'll post them.

Seemingly relevant specs: Dual 1920x1080 monitors on a dedicated NVidia card, Ubuntu 13.10 64-bit. This does not happen on my laptop (32-bit 13.10, same software and updates installed, no external monitor).

Any help tracking this issue down would be greatly appreciated!

---

