---
title: "autohidden 1 pixel gnome panel stopped unhiding"
date: 2009-04-01
forum: General Help
---

### Post by redsun82 on 2009-04-01
Using a dock, I had successfully hidden the panel as much as I could (I still wanted to keep a pair of applets and the Linux Mint menu in it) by setting it to auto hide and setting the autohidden size to 1 pixel. All went well for some five months. I got my mouse to the top edge and the panel reappeared.

Now (probably due to an update but I still was not able to trace which) this stopped working. The 1 pixel strip is there, but going to it with the mouse does not unhide the panel. Experimenting I noticed that now the autohidden size needs to be at least 4 pixels to get the unhiding. This is quite annoying, more so as it worked fine before.

Has anyone encountered something similar?

Cheers!

---

### Post by redsun82 on 2009-05-15
Problem is still here. Baffling: my computer at the university has the same setup (same distro, which is Linux Mint Felicia btw, same gonf settings for the panel), and there it works. On my laptop still no luck. Anyone?

---

### Post by Scoobin on 2010-02-25
I'm also having this problem lately (on 9.10). I'm using AWN as well but sometimes you need a hidden panel handy. 

To access the panel the only way I know is to type in a terminal:

```
gnome-panel --replace
```

and then I have to quickly right click it when it pops up for a second before hiding again. Then I have to untick autohide if I want to access it, but in the long term I don't want the panel revealed by default.

---

### Post by sjhaffner on 2010-10-10
Yup same problem. An auto hide panel is always hidden now!  :(

---

### Post by sjhaffner on 2010-10-10
I found a way to make it not auto hide! so at least it is usable =)

4th post:
[http://ubuntuforums.org/showthread.php?t=1328349 ]("http://ubuntuforums.org/showthread.php?t=1328349")
This thread has a script to auto-hide with a key command. Seems like a lot of people are having this problem.

4th post:
[ http://ubuntuforums.org/showthread.php?t=1345815]("http://ubuntuforums.org/showthread.php?t=1345815")

Hope this helps!!!

---

