---
title: "Freeciv wont let me start a game!"
date: 2005-07-08
forum: Gaming &amp; Leisure
---

### Post by fizgig on 2005-07-08
I want to try this game out and I installed it through synaptic and it seemed to install ok.  I select "freeciv" in the game menu and I get the first screen.  I select "Start New Game" and it freezes.  Nothing else happens.  Anyone know what I could have possibly done wrong?

---

### Post by fizgig on 2005-07-08
I'm the only one with this problem?  :-?

---

### Post by Takis on 2005-07-08
Are you running a freeciv server?

---

### Post by fizgig on 2005-07-09
Not intentionally...  But, when I start a game, I see from the list of processes that it's trying to start one:

14077 ?        00:00:00 civclient-gtk
14078 ?        00:00:00 civserver

---

### Post by Takis on 2005-07-10
Yeah it's supposed to be running during a game. I don't really know much about how freeciv works, but try running a server first (before starting a game). In the meantime, I'll try and install it today or tomorrow and get back to you.

---

### Post by fizgig on 2005-07-13
The freeciv guys emailed me and they figured out the problem:

My loopback interface was down so I couldn't ping localhost.  A simply **sudo ifup lo** brought it up and I can play!

Next question: how to get the lo interface to always come up.  I've started a [thread]("http://www.ubuntuforums.org/showthread.php?t=48557") relating to that.

---

