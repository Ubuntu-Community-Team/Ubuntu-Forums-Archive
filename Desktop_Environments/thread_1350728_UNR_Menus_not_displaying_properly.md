---
title: "UNR Menus not displaying properly"
date: 2009-12-09
forum: Desktop Environments
---

### Post by EpsilonEX on 2009-12-09
I run Ubuntu 9.10 Netbook Remix and I had deleted a shortcut from favorites and now all of my menus in the netbook desktop environment are messed up. Many shortcuts I can't get to because they are hidden beyond the scrollable area including the one to switch to the standard desktop and shortcuts are only three wide instead of the usual four. I'm not particularly experienced in Linux so I don't know of any way to change it through commands or anything.

A couple of screenshots of my problems:
[IMG]http://imgur.com/EegH7.png[/IMG]

In the favorites menu in the screen shot above I can't add any more because they end up being displayed beyond the area where I can scroll down.

[IMG]http://imgur.com/ItuUn.png[/IMG]

In this screen shot of the System tab the icons are overlapping and there a bunch that cannot be accessed. The top six icons seem to display fine but the three immediately following that have a selectable area that extends far below where the icons should be, an entire screen height space exists between the first nine and the rest of the icons which you can see above.

---

### Post by EpsilonEX on 2009-12-19
Still needing help with this. Some programs are unaccessible to me.

---

### Post by EpsilonEX on 2009-12-21
If anyone has any better suggestions where I can get some help it would be great.

---

### Post by erlguta on 2010-02-07
Everyone has this problem. To me this is a very serious bug that highlights the lack of professionalism of the UNR project developers  for release it with this bug.

This is the bug related:
[https://bugs.launchpad.net/ubuntu/+source/netbook-launcher/+bug/435805](https://bugs.launchpad.net/ubuntu/+source/netbook-launcher/+bug/435805)

Months and months and we dont now nothing about if somebody is working on it...

---

### Post by erlguta on 2010-02-07
Wow!. I think i soved it.
I had installed 'htop' program that put another section 'System tools' in the lateral menu. So i edited the menu and disable the programs in the 'system menu'...in this case only 'htop' program and Voila!...now all my icons looks fine in System -> Administration

---

### Post by albesan on 2010-04-16
Hello team,

I have this problem and removing sections from the main menu does not make a difference. There are both overlaping icons and icons out of sight at the bottom.
I have been searching but can´t find a solution.
Any ideas appreciated, thanks

---

### Post by erlguta on 2010-04-16
The bug related is this:
[https://bugs.launchpad.net/bugs/435805](https://bugs.launchpad.net/bugs/435805)

It seems that is going to be fixed in Lucid.

---

