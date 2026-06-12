---
title: "Mouse Unresponsive when pushing multiple keys on keyboard"
date: 2008-02-16
forum: Desktop Environments
---

### Post by Alpha7 on 2008-02-16
I just installed Ubuntu 7.10 about a week ago with a couple of friends of mine to play around with it and to see what we could all get working in it. So far we have each been having our own unique problems. Last night however we decided to mess around and try some games for a little break. We all downloaded Sauerbraten and once we got into the game we noticed that if we were moving and strafing (essentially holding two keys on the keyboard at the same time) that anything we did on the mouse was completely ignored until we let off the keyboard. 

All 3 of us had this problem and we searched a bit last night for a solution but found nothing.

Now we all have 3 different systems, I have an ATI card with newest drivers, another has an Nvidia and the other has some generic Intel card.

After discovering this we tested it on the normal Ubuntu gnome desktop and found the same thing happens. If two keys are held down and the mouse is moved or click the mouse doesn't respond until the keys are unheld. 

I am wondering if there is a fix to this problem as it appears to be something affecting all Ubuntu 7.10 users from the initial install.

---

### Post by Alpha7 on 2008-02-17
Anyone...?

---

### Post by Alpha7 on 2008-02-19
> **Alpha7 said:**
> Anyone...?

bump

---

### Post by Steveway on 2008-02-19
Doesn't happen here. So it is not a generic Ubuntu Problem.
It sounds more like a hardware-problem what peripherie is giving you problems?

---

### Post by Alpha7 on 2008-02-22
Well, I mean its my mouse that is not responding, but only for as long as I hold down multiple keys on my keyboard. For example, If i wanted to copy and paste, I would hold down 'ctrl + v' while I am holding down these two keys, my mouse is completely unresponsive. If i wanted to play a FPS, Where the movement keys where 'WASD' If i wanted to move forward and side to side (holding 'W' and 'A' or 'D' My mouse would be unresponsive until I let go of one of the keys.

As I mentioned above, This was tested on 3 computers, One had USB Keyboard and mouse, other USB and PS2, Mine has both PS2. Same results on each computer.

---

### Post by Alpha7 on 2008-02-23
bump

---

### Post by blastermaster on 2008-02-25
I have the same problem, I cant play games while using keyboard and mouse, and in the desktop if i press any key the mouse cursors just halts anyone have a fix for this thanks.

---

### Post by Alpha7 on 2008-02-25
Good to know I'm not the only one who has seen this problem. Sadly the fact of the matter is that its been over a week and no one has shown any effort or interest in helping me solve this problem.  I would think that such a developed OS such as Ubuntu would be able to support simultaneous mouse and keyboard input. 

I thought the Ubuntu community would be more helpful. So far I've been proven wrong. The main reason I have a computer is to play the occasional game and if I can't do that there is no point in using Ubuntu, so I would like to get this solved.

Also note, this doesn't appear to affect laptops at all, keyboard + mouse work fine on my laptop with Ubuntu, and its configured exactly the same as my desktop.

---

### Post by Alpha7 on 2008-02-28
Blaster.... I found two processes both called 'mouseemu' that were running on bootup. After killing these processes. my mouse and keyboard started working together. Let me know if you have any more problems or this doesn't fix it.

---

### Post by SoulinEther on 2008-06-18
Excellent - you've solved my problem.

The question still remains, however... why is mouseemu running at all?

---

