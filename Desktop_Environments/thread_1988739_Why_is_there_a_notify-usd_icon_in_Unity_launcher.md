---
title: "Why is there a notify-usd icon in Unity launcher?"
date: 2012-05-28
forum: Desktop Environments
---

### Post by welshmike on 2012-05-28
A notify-usd icon (a question mark inside a square) has appeared in the Unity launcher for 12.04.
What is it please?
Also I've not been able to remove it from the launcher.

---

### Post by zombifier25 on 2012-05-28
Can you take a screenshot of it and post here? Since it's hard to figure out what it is with only description.

---

### Post by welshmike on 2012-05-28
OK. Will do next time it occurs.

---

### Post by welshmike on 2012-05-28
Below in the screen image. Note the square with the ? in it.
Also 12.04 seems rather buggy still. System hangs from time to time requiring a re-logon.
[IMG]http://www.winchesternw.org.uk/notify-osd.png[/IMG]

---

### Post by fragos on 2012-05-28
Right click the "?" icon and the associated application name will be displayed. The reason for the "?" is that the specified icon in the .desktop file can't be found.

---

### Post by zombifier25 on 2012-05-29
Yep. That icon belongs to an application that does not have an icon.

---

### Post by welshmike on 2012-05-29
Thanks for the replies.

Arghh! The mystery is now bamfdaemon. Also why does my desktop (cropped below) have a small white square to the right of the Dash icon?
[IMG]http://www.winchesternw.org.uk/bamfdaemon.png[/IMG]

---

### Post by Frogs Hair on 2012-05-29
I don't what the white square is and I have never seen an icon for a daemon displayed in unity in any release . You could try to reset Unity.```
unity --reset
```

---

