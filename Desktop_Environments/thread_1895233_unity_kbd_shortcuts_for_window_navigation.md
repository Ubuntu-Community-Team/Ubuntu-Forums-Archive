---
title: "unity: kbd shortcuts for window navigation?"
date: 2011-12-14
forum: Desktop Environments
---

### Post by butters on 2011-12-14
I finally bit the bullet and installed a plain vanilla Ubuntu 11.10 with the default Unity shell. I'm trying to set up an efficient window navigation scheme, but I can't immediately figure out how I would get what I want from the keyboard shortcut dialog in the system settings application. I can't even figure out how to edit shortcuts in this dialog. I click to highlight a shortcut action and hold my preferred key combination, but it doesn't work.

I have two terminal windows tiled side-by-side with multiple terminal tabs in each window. I can navigate through the tabs in each window using Ctrl+PgUp/PgDown, which is the default tab navigation within the terminal application. There is also Shift+Ctrl+PgUp/PgDown to move tabs left and right within the terminal application's window.

I would like to use Ctrl+Alt+PgUp/PgDown to navigate (shift focus and raise if covered) between my two terminal windows, or in general through the active windows on the current workspace. How do I make that happen?

Note: Alt-Tab is not what I'm looking for. I don't want any graphical widget to pop up. I don't want this navigation mode to consider minimized windows or windows on other workspaces.

---

### Post by thaelim on 2011-12-16
Someone may correct me, but the window management keyboard shortcuts in the System Settings panel are only applicable if you are running Gnome Shell. To tweak Unity's shortcuts, you need compizconfig-settings-manager. There are numerous places in that app where you can tweak keyboard shortcuts to your hearts content.

---

