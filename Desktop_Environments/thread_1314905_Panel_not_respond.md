---
title: "Panel not respond"
date: 2009-11-04
forum: Desktop Environments
---

### Post by ckinsung on 2009-11-04
What I did to the panel was only choose to auto hide it , but after restarting my computer, the panel freeze and I cannot see it on the desktop. I can't access all the applications . etc.. How can I restore my panel setting? 

[IMG]http://i6.photobucket.com/albums/y246/ckinsung/Screenshot1.png[/IMG]
[IMG]http://i6.photobucket.com/albums/y246/ckinsung/Screenshot2.png[/IMG]

---

### Post by ckinsung on 2009-11-04
> **ckinsung said:**
> What I did to the panel was only choose to auto hide it , but after restarting my computer, the panel freeze and I cannot see it on the desktop. I can't access all the applications . etc.. How can I restore my panel setting? 

[IMG]http://i6.photobucket.com/albums/y246/ckinsung/Screenshot1.png[/IMG]
[IMG]http://i6.photobucket.com/albums/y246/ckinsung/Screenshot2.png[/IMG]

As you can see from the second picture, when I tried to restart my computer, a screen saying that my panel is not working. I usually put my panel at the bottom rather at at the top(default), but you see that the default panel disappears at the bottom.

---

### Post by ckinsung on 2009-11-04
I tried with 


sudo debconf gnome-panel

it doesn't work.

---

### Post by ckinsung on 2009-11-05
About 9 hours before, I managed to get some helps and it worked perfectly. 

gconftool-2 --shutdown && rm -rf ~/.gconf/apps/panel && pkill gnome-panel

Thank you for your helps also.

---

### Post by kongstad on 2009-11-13
I had the same problem, and your solution worked.  I couldn't find a bug report in it, so I created a new bug.   [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/481643](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/481643)

---

### Post by HT12g on 2011-02-23
> **ckinsung said:**
> About 9 hours before, I managed to get some helps and it worked perfectly. 

gconftool-2 --shutdown && rm -rf ~/.gconf/apps/panel && pkill gnome-panel

Thank you for your helps also.

Thank you very much! It fixes the gnome-panel bug on my laptop perfectly.

---

### Post by Copper Bezel on 2011-02-24
I know this thread is solved, but a quick question if I might - did you have any Compiz edge bindings active of any kind? I've had problems before with conflicts between the two.

---

