---
title: "KDE and multiple displays == serious problems with focus"
date: 2007-11-20
forum: Desktop Environments
---

### Post by tavasti on 2007-11-20
I just installed Kubuntu 7.10 to my workstation. I had tested it first
on my laptop, KDE seemed to have features I need. Or that is what I
thought. 

Unfortunately, KDE doesn't work properly with multiple displays. I
have 3 monitors without xinerama. I extencively use several desktops,
and try to do everything without mouse. This set seems to be poison
for KDE. When usin keyboard shortcut for changing to another desktop,
focus is very commonly lost to another display. If I try to move 3
dekstops to right on display :0:0, I most likely end up changing
desktops on :0.1 or :0.2. This is when I have focus policy 'click to
focus' or 'Focus follows mouse'. 

When setting 'Focus under strictly under mouse' behaviour is better,
but unfortunately that setting is nearly brain-dead. Changing active
application with alt-tab doesn't move pointer to selected window. 
No problem if you are running only full-screen apps, but I tend to have 
plenty of smaller windows. So with that setting it's impossible to use keyboard for
changing active window. 

Do I have to switch back to fvwm? Xinerama would solve also problem,
but that is not suitable solution for me. If I need access to software
X on display 1, I want to keep same apps visible on displays 2 and 3.

---

### Post by firephoto on 2007-11-20
Do you have three individual desktops or is the desktop spanning all three? This wasn't very clear and 'xinerama' seems to have a bit of a different meaning depending on what kind of video card(s) someone is using.

I had to use some of the options I found on this page with kubuntu since there isn't a configuration dialog available and it was easier than messing around to re-enable them for kcontrol.
[http://ktown.kde.org/~seli/xinerama/](http://ktown.kde.org/~seli/xinerama/)

---

### Post by tavasti on 2007-11-20
Separate desktops. DISPLAY :0.2 on left, 0.0 on center, and 0.1on right. One dual-head Matrox G400, and one PCI Millenium II.

I don't want one big desktop, but 3 separate. That's reason why I don't want xinerama. Or is there some way to make separate desktops 
to xinerama screens? With separate desktops I mean possibility to have own, separate pager for each screen.

---

