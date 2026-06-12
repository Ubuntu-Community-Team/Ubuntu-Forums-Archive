---
title: "KDE, Compiz, Plasma and pager issue"
date: 2009-04-15
forum: Desktop Environments
---

### Post by Memes11 on 2009-04-15
Hello,

I just switched to KDE desktop and I fall in love with it (The previous KDE I used was ugly). I am then now using KDE 4.1 (the default in Kubuntu) and I got some issues. the most important one is concerning compiz.

I setted up compiz to start automatically at the startup (I added 'Compiz --replace' in the autostart list, maybe not the right way to do...). When my computer starts, it displays an error complaining about a SIGABRT problem (see here for similar issue : [Link]("http://markmail.org/message/dmerl6z2vnfbo44s?q=compiz+sigabrt&page=1&refer=uqgzxaoeg6z3xivj")), the pager also displays only one desktop (while I actually have 4).

If I click on OK to close the error message, then close my pager widget, and add a new pager, it works flawlessly...

To be noted too, there is no way to change the config of the initial pager.

Does anyone can help me?

Thanks

---

### Post by txcrackers on 2009-04-16
KDE has it's own compositing built into the window manager and this usually causes problems with Compiz. I'd suggest removing Compiz and use the built-in facilities. They get even better in 4.2

---

### Post by Memes11 on 2009-04-16
> **txcrackers said:**
> KDE has it's own compositing built into the window manager

May you tell  bit more for a pure noob like me?

Does it has the cube too (I particularly like this one :))

---

### Post by Monsieur Gonzalez on 2009-04-16
Yes, cube effect is there too (and many other things, more info [here]("http://www.kde.org/announcements/4.2/guide.php")). Take txcrackers's advice and update to 4.2.2 (see the kubuntu guide on how to get the updates, or wait till Jaunty).

---

### Post by Memes11 on 2009-04-17
Merci Monsieur. 

I had a look on it, I can not find the cube yet (but you said it is there, I will continue to look for it).

Disabling compiz indeed solve the issue (no surprise ;))

Is there a way to keep kwin for KDE but to have compiz activated for Gnome (if ever I decide to boot with gnome).

Thanks

---

### Post by Monsieur Gonzalez on 2009-04-17
1- Cube effect - Go to System Settings, Desktop, Desktop Effects, All Effects tab, enable the Desktop Cube (activate it with Ctrl+F11). I had to disable Desktop Grid.

2- You can keep Compiz, you can use it in your Gnome session.

---

### Post by Memes11 on 2009-04-18
I did not find it under KDE 4.1 and then update to KDE 4.2, it is great. I actually prefer this cube :)

KDE Is really a good surprise for me :)

---

