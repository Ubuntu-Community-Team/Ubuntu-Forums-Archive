---
title: "Mapping key to run small program"
date: 2015-12-30
forum: Desktop Environments
---

### Post by NuxNik on 2015-12-30
Hello,

I have to use an browser-based application that is slow. When updating, it requires multiple repeated (left) mouse clicks that are naturally delayed because of server processing delay.

I would like to write a small Perl or C program and map it to a unique keystroke so that if ever that particular keystroke is used my little program would do the following:

1) on current mouse location enter left-click
2) wait t milliseconds (where t is hard coded in program)
3) Loop n times (where n is hard coded in program)

I would like to trigger this with the Special key (also known as the Windows key) + click of the scroller button on the mouse (which supposedly is button 2)..

I have tried autokey, and there are all sorts of issues using it, that basically make it unworkable

I want this mapping to work for ANY and ALL X11 applications, so it has to be triggered the lowest level.

Suggestions, advice appreciated
If this is inappropriate venue, recommendations to more appropriate venue also appreciated.

TNX

---

