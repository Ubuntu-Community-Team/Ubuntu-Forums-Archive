---
title: "Problems with Compiz-Fusion."
date: 2007-11-04
forum: Desktop Environments
---

### Post by ignorance on 2007-11-04
I have 2 problems with compiz

1) On my laptop everything works, as long as i don't restart my laptop than i have the following problem:
[http://img511.imageshack.us/my.php?image=screenshotyg5.png](http://img511.imageshack.us/my.php?image=screenshotyg5.png)
And i would like it to be:
[http://img264.imageshack.us/my.php?image=screenshot1rv5.png](http://img264.imageshack.us/my.php?image=screenshot1rv5.png)
The laptop is an HP NX 7400
Link to the specs:
[http://www.intel.com/products/chipsets/gma950/index.htm](http://www.intel.com/products/chipsets/gma950/index.htm)

2)This problem is situated on my desktop. Since i didn't had the option to activate the compiz part i had to use something like fglrx or xgl. Now compiz is working great no problems at all. Only when i turn it off that's when the problem starts. The whole system just gets really sluggish. For example when i try to play the next song on xmms-player it takes like 2 minutes before he reacts and plays the next song.

---

### Post by ggaaron on 2007-11-04
I think I don't understand your post... Could you explain more clearly what you did to get compiz and how do you turn it off?

---

### Post by ignorance on 2007-11-04
Left click on desktop select Change Desktop background > Visual effects. And there i can turn everything off and on.

By compiz i mean the default thingy on ubuntu Gutsy Gibbon

---

### Post by ggaaron on 2007-11-04
Hmm. Try to turn compiz off by running (for example from Alt-F2 popup run app) "metacity --replace". And see if it is still so slow... If yes, then try to turn on compiz by running "compiz --replace" - better do this in a terminal, so you can see what got wrong.

---

### Post by Mellon on 2007-11-04
maybe is a good idea to try another theme.... good luck

---

### Post by ignorance on 2007-11-07
> **ggaaron said:**
> Hmm. Try to turn compiz off by running (for example from Alt-F2 popup run app) "metacity --replace". And see if it is still so slow... If yes, then try to turn on compiz by running "compiz --replace" - better do this in a terminal, so you can see what got wrong.

Tried that and that does not help anything. And the terminal didn't post any errors.

> **Mellon said:**
> maybe is a good idea to try another theme.... good luck

And why should that help? The problem doesn't excist within the themes but with my graphics thingy.

---

### Post by ggaaron on 2007-11-07
Try to turn off compiz and then run top from command line or your favourite monitoring tool (as gnome-system-monitor) and see what is taking the cpu. It can be nautilus, sometimes it does such things.

---

### Post by dmazzone on 2007-11-07
I had a similar problem on my HP Pavillion laptop when I installed Gutsy.I fixed it by editing the default font size for the title bar with the gconf-editor, that seems to have done the trick. If anyone knows why this is happening or a better solution please let me know.

Hope This Helped :)

---

### Post by ignorance on 2007-11-08
> **dmazzone said:**
> I had a similar problem on my HP Pavillion laptop when I installed Gutsy.I fixed it by editing the default font size for the title bar with the gconf-editor, that seems to have done the trick. If anyone knows why this is happening or a better solution please let me know.

Hope This Helped :)

Well, if i can figure out where i can find the default font size being set with compiz this could help. Perhaps i can add that the problem only excists when i use compiz :).

> **ggaaron said:**
> Try to turn off compiz and then run top from command line or your favourite monitoring tool (as gnome-system-monitor) and see what is taking the cpu. It can be nautilus, sometimes it does such things.

To be honest that didn't crossed my mind but i will paste it later here.

---

### Post by ignorance on 2007-11-09
> **ggaaron said:**
> Try to turn off compiz and then run top from command line or your favourite monitoring tool (as gnome-system-monitor) and see what is taking the cpu. It can be nautilus, sometimes it does such things.

To be honest that didn't crossed my mind but i will paste it later here.

Now i tried that and the cpu didn't went above 10% usage. Can the problem be suited at my graphics card?

---

