---
title: "Run App/Command from Lock Screen"
date: 2023-07-03
forum: Desktop Environments
---

### Post by aaroncampbell2 on 2023-07-03
I have a little [Python script that I wrote to control my Elgato Key Light]("https://github.com/aaroncampbell/elgato-key-light-control"). I'd like to be able to run it from the lock screen. When logged in, `elgato toggle` is set to `Ctrl+Super+L`, but I don't care if I need to click an icon or maybe there's a way to add it to the power menu (that seems to be visible on that screen). Essentially, is there any way to allow a specific command to be run from the lock screen?

I'm on Ubuntu 23.04

---

### Post by TheFu on 2023-07-04
Asking for "any way" ... usually isn't productive.  There are many, many, "any way" options with enough time, effort, expertise, you can do anything.
I don't know of any easy way.  Any keyboard input should be limited to the 2 fields used by the lock screen.

You could add your program to a custom lock screen, but there are security implications in modifying code that implements key security features. Many times people who modify that code open all sorts of security flaws.

For example, allowing "a specific command to be run from the lock screen" ... could easily provide root access to a system, if handles wrong. That wouldn't be good.

---

