---
title: "Couple of questions regarding Window Manager"
date: 2005-12-16
forum: Desktop Environments
---

### Post by Redindian on 2005-12-16
Recently, I have installed windowmaker window managers via synaptic.  Now I have gnome session and Wmaker session at the login or startup. Whenever i login using gnome, i'm in default metacity WM (1) How can i change from default metacity to default Wmaker? (2) If i login using Wmaker (selected from sessions), does this mean i'm using Wmaker under gnome desktop environment? I think i'm confusing. Could anyone please answer my 1st question and clarify me the 2nd?
Thanks.

---

### Post by iansyngin on 2005-12-16
At the screen where you login there is a session section.
here you can choose a default window manager etc

---

### Post by Redindian on 2005-12-16
iansyngin,
Thanks but your reply didn't answer/clear my doubts. Anyone know how to change the default metacity WM to Wmaker WM?

---

### Post by afhp on 2005-12-16
[QUOTE=Redindian]If i login using Wmaker (selected from sessions), does this mean i'm using Wmaker under gnome desktop environment? I think i'm confusing. Could anyone please answer my 1st question and clarify me the 2nd?
Thanks.[/QUOTE]

I'm not familiar with GDM specifically, but considering that most session managers work the same... When you log in with "Gnome session" it does just that, (re)start the Gnome session with whatever window manager Gnome uses (Metacity at that point). When you log in with "Window Maker" it is *only* the window manager, it doesn't start the Gnome environment. 

Also note that a) Window Maker has its own session management, i.e. when you leave and go back wmaker should remember what you were running on which screen, etc. b) if you start a Gnome program from within Window Maker it should  automatically load whatever parts of Gnome are required (in any case that's the way KDE works). 

If you do want the full Gnome environment with Window Maker (your first question) someone else will have to answer, I can only confirm that you can do it.

---

### Post by Redindian on 2005-12-16
Thanks afph. 

Anyone have any idea about how to make Wmaker as default WM in GNOME?

---

### Post by shakin on 2005-12-17
[QUOTE=Redindian]Thanks afph. 

Anyone have any idea about how to make Wmaker as default WM in GNOME?[/QUOTE]

Follow the guide for [Enlightened Gnome](http://www.ubuntuforums.org/showthread.php?t=54476), but change the --default-wm from enlightenment to wmaker. You might want to try with enlightenment as the window manager as well, just for fun.

---

### Post by Redindian on 2005-12-17
Thanks shakin. I tried E16 under gnome, its working great now. I used the same procedure to make Wmaker as dfault gnome WM but it didn't work.

---

