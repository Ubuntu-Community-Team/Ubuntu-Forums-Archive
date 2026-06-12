---
title: "n00b question (resoluton)"
date: 2005-09-02
forum: Desktop Environments
---

### Post by shinku on 2005-09-02
I have a very old 14" monitor.  After I installed ubuntu, the display started acting bizzarely (displaying 4 "desktops" squished together).  I think it may have been caused by the resolution.  Where is the dialog to change the resolution?  I can't seem to find it.
(btw, I read the wiki...  it isn't in there either)

---

### Post by KingBahamut on 2005-09-02
Might have an unsupported monitor or card. 

whats the make and model of both your graphics card and monitor. 

You will most likely need to edit your /etc/X11/xorg.conf file a bit.

---

### Post by shinku on 2005-09-02
The monitor is an Orchestra,  I'm not sure what the video card is but the computer is an AMD so it could be integrated.

---

### Post by d1337 on 2005-09-03
Thought someone else may be able to help you more than I can...but a couple of questions.  Does this only happen in X or are you able to access a terminal via ctrl+alt+f1?  I'm assuming that you have another machine on the net or that this is a dual boot setup.  If you can get to a terminal, an lspci from a command line may tell us a bit more about your video card, but looking at the back of your box should determine integrated video or an added card.  Does your monitor have sync rates on the label?

d1337

---

### Post by shinku on 2005-09-03
[QUOTE=d1337]Thought someone else may be able to help you more than I can...but a couple of questions.  Does this only happen in X or are you able to access a terminal via ctrl+alt+f1?  I'm assuming that you have another machine on the net or that this is a dual boot setup.  If you can get to a terminal, an lspci from a command line may tell us a bit more about your video card, but looking at the back of your box should determine integrated video or an added card.  Does your monitor have sync rates on the label?

d1337[/QUOTE]
 I'm not at the house with that computer today, but I will be there on Monday.  I will look at the monitor/box then and post additional info.  I can access the terminal, its a bit odd looking but still mostly readable.

---

