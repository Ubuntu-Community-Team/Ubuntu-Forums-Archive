---
title: "Xmonad in Gnome"
date: 2009-12-31
forum: Desktop Environments
---

### Post by bgc on 2009-12-31
Hi, I am aware that this post should belong in an Xmonad-specific forum, but most Xmonad posts I have seen are in Ubuntuforums. I have recently started using Xmonad as a window manager (replacing Metacity). I use the standard configuration file suggested on the Xmonad website for integration with Gnome. It is brilliant, I have to say, except for the fact that I find it to be very unstable. It crashes quite frequently. The most evident case is when opening Open Office documents. By crashing I mean that non of the keyboard shortcuts work, and when opening any other window, the borderless window is placed over the Gnome panel. It can be reset by opening a terminal and reissuing the 'xmonad' command, in which case all open windows are put back into the first workspace. Does anyone know why this might be the case? I don't know how to describe the issue more specifically. Any indications would be very welcome!

Thanks,

bgc

---

### Post by PAKSHAN on 2010-01-05
[FONT=arial]its unlikley that this will ever change. ****There are separate tools, which I recently learned about that can assist me with this. For example the perl script '[wumwum]("http://wumwum.sourceforge.net/")'. But this seems to be the wrong solution to a real problem. Additional wumwum does not work properly with metacity and so I'd need to another WM anyway, which lead to the point where I started thinking about integrating a true tiling wm into GNOME... once again.

First, I looked into awesome, which is a window manager I used some time ago.
But documentation about configuring it is basically an API documentation, with no obvious entry point.
It seems to be the best to study the whole API just to set some simple settings (e.g. a padding for the GNOME panel and some always-floating applications). I even thought about learning LUA, because it seems like a language which is quick and easy to learn, but honestly if I need to study a programming language and a whole API documentation just to configure a window manager then IMHO there is something conceptionally wrong with that piece of software.
================================
[LIMS Software](http://labface.com/suppliers/LIMS-Software-33)
[affiliate guide](http://www.affiliateleap.com/)

[/FONT]

---

### Post by bgc on 2010-01-14
Maybe you misunderstood me. My experience with Xmonad so far is very good, and that is using their standard configuration file for Gnome (I have no clue of Haskell). It is very much what I was looking for. Of course, it coud be even better, and if I could alternate easily between Metacity and Xmonad, for instance, it would be even better, but that is asking a lot. My issue is that Xmonad is, according to most people, surprisingly stable, and yet I find it crashes quite regularly. A situation that repeats itself is opening Open Office documents. Xmonad crashes, and only the active window can then be used. If you're lucky, the active window will be a terminal from which you can restart Xmonad, otherwise you need to log out and back in. This is the only frustrating issue for me.

The next step is to understand just basic Haskell to tweak the configuration to better suit my needs, but that is looking like a longer-term project for now!

---

