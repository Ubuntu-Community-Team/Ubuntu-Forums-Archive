---
title: "Keyboard Input not accepted sometimes"
date: 2009-07-22
forum: Desktop Environments
---

### Post by keroro on 2009-07-22
I got two different systems. A Desktop PC with Kubuntu 8.04 and a laptop with Ubuntu 9.04. On both systems (especially on the laptop) I got the problem that some applications suddenly do not accept keyboard input anymore. It means I want to type an URL in Opera and nothing happens. I have to click on another open application first, then go back to Opera and it works again.
It mainly happens on Opera, Inkscape, Thunderbird, Skype and Netbeans. On Netbeans it happens each time I run a program. After closing the window of the program I tested, I can not put any text into the active tab on Netbeans. I first have to click another tab in Netbeans and the go back to my original tab to make keyboard input work.
I got SCIM installed.

---

### Post by auklet2k on 2009-08-08
I have encountered such situations too. I couldn't even use either IDLE, eclipse and netbeans. Once I typed the name of a function, IDLE shows the usage of function. Later, the keyboard seems to be dead when the little helper window closed. I had searched a lot, but no threads helped.

In fact, I have my own theory about this issue. When I type words in eclipse for example, it pops up a helper window to show some info in context. Once my words has done, the poped window destroyed, but the input focus doesn't return to parent window, viz, Xserver doesn't think it's time for the parent window to get input focus. Here comes the problem.

My box is running Kubuntu 9.04 official release. But I spotted this problem since 8.10 or 8.04. I used eclipse in the past and it ran well. I think the problem comes by new updates of Xorg.

---

### Post by kruykaze on 2009-11-01
This got worse with karmic :( can't type anything in grooveshark.com

---

