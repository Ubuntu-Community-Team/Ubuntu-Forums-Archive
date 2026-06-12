---
title: "Emerald problems"
date: 2009-01-02
forum: General Help
---

### Post by linuxlover15 on 2009-01-02
Okay, I decided to use Emerald for a change. I installed the emerald package, and then I went to the terminal, and put "emerald --replace". Well, when I did that, the bar that has the close, minimize, maximize buttons on it would change, but when I would close out a window the bar would disappear. I'm not sure if this is a bug, or something. If there is a way to stop this from happening please help.

---

### Post by L8erG8er on 2009-01-02
I use Emerald successfully, but I'm not sure I understand the problem you're having.  Can you explain further?  Which bar is disappearing?

---

### Post by GeorgeMurango on 2009-01-02
Your problem is that you're running the command in a regular terminal. When you close out of it, it stops the command. Hit alt+F2, then type "emerald--replace" there. Or go to sessions under preferences, and add "emerald--replace" there to make emerald skin your windows on startup.

---

### Post by paris_alex on 2009-01-02
i think i understand your problem. you should type "emerald --replace &" instead of "emerald --replace". I'm guessing the emerald process was killed when you close the terminal screen or exit the command.

Hope this helps.

---

