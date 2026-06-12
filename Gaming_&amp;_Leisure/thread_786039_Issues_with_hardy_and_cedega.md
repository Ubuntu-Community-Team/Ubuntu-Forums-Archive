---
title: "Issues with hardy and cedega"
date: 2008-05-07
forum: Gaming &amp; Leisure
---

### Post by Pnut on 2008-05-07
Hello all,

I've been experiencing an issue with video when attempting to play video games using cedega.  I can run Eve Online just fine, but when I try to run other games such as Jedi Academy, Generals/ZeroHour, I can hear the the games start up fine, but my monitor says, "over range" every time.  My games worked flawlessly in Gutsy with cedega.

I tried Ubuntu starting with Breezy Badger, and I haven't touched a windows box since.

Please help as I am developing a twitch without my video games.

Pnut

---

### Post by eragon100 on 2008-05-08
Yeah I had that problem as well with some of my native games, it drove me nuts.

The problem is that after you install the restricted video drivers, at least on nvidia cards, ubuntu starts using the "generic monitor" driver for your monitor. This results in wrong refresh rates. In my case, the monitor stated "input not supported", in your case it says "out of range". Solvable very easy with the screens and graphics program. Since this has been removed from the menu in hardy, open a terminal and enter the command:

sudo displayconfig-gtk

Offcourse type in your password, and then screens and graphics should appear.
At model it "should" say generic monitor.

Click on that and select the manufacterer and model of your monitor in the list that appears. Select desired resolution and refresh rate and close the screen with ok.
Restart the computer and everything should work.

Have fun! :)

---

### Post by Pnut on 2008-05-08
thanks for reply,  My monitor is a Sceptre X7 and isn't listed in the list of manufactures.  Any idea on where to go next?


Pnut

---

### Post by Pnut on 2008-05-08
lol, sorry for dumb reply, i got it working, thank you for your prompt reply and very detailed description.  The ubuntu community is why i run this os. ( aside from the obvious windows problems and reasons)

Pnut

---

