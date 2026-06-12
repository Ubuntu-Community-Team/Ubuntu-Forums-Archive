---
title: "Focus Lost, Keystrokes Discarded - sundry issues"
date: 2010-04-30
forum: Desktop Environments
---

### Post by clubsoda on 2010-04-30
In Xubuntu Lucid, such as:-

**1) Focus doesn't return to originating window. Can't type.**
Start an application from a terminal window, e.g. play a media file with vlc.
Quit the application.
Focus appears to return to the terminal (title bar highlighted) but subsequent keystrokes are dropped.
Clicking on the terminal window doesn't help. Need to click somewhere else first and then click back onto the app.

**2) Notifier breaks focus.**
Be typing away happily into some application, editor etc.
Notifier pops up with some important message.
Application appears to retain focus but any further keyboard input is ignored.
Need to click off, click back on the application.

**3) Mouse-wheel scroll of background application steals focus.**
When it works, this is a luxury feature - the ability to scroll a background window (such as a browser) while editing a document or spreadsheet in the foreground.
Now, however, the background application is brought forward and given focus if a mouse-over scroll action is attempted.

Any suggestions?

---

### Post by sav2005 on 2010-05-04
[QUOTE=clubsoda;9203683]In Xubuntu Lucid, such as:-

**1) Focus doesn't return to originating window. Can't type.**
Start an application from a terminal window, e.g. play a media file with vlc.
Quit the application.
Focus appears to return to the terminal (title bar highlighted) but subsequent keystrokes are dropped.
Clicking on the terminal window doesn't help. Need to click somewhere else first and then click back onto the app.



I'm seeing this behaviour in Emacs, using the Gnome desktop flavour of Lucid Lynx.

---

### Post by clubsoda on 2010-05-06
I just wanted to add that problems 1) and 2) affected my KDE and Gnome as well, not just Xubuntu. However, 1) and 2) are now fixed on my system for all flavours.  I believe the fix came after I adjusted the language/locale settings.

I'm still seeing problem 3) but only on Xubuntu.

Cheers.

---

### Post by fejalish on 2010-07-04
Just found a solution to number 3. (It had been bothering me ever since upgrading to 10.04.) You can found it here: [http://www.mail-archive.com/pkg-xfce-devel@lists.alioth.debian.org/msg05843.html](http://www.mail-archive.com/pkg-xfce-devel@lists.alioth.debian.org/msg05843.html)

---

