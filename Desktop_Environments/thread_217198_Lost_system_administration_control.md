---
title: "Lost system administration control"
date: 2006-07-16
forum: Desktop Environments
---

### Post by Zingomoos135 on 2006-07-16
i was changing my users information so that my account didn't have control over system administration stuff, and realized how stupid that was, and meant to press "cancel" but i pressed "ok" instead, now NO USERS HAVE ADMINISTRATION CONTROL! i don't know how to change it back so that i have admin control again!

PLEASE HELP ME!

---

### Post by aysiu on 2006-07-16
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by Zingomoos135 on 2006-07-16
i'm sorry... i'm really new to linux and i don't really know what to put in the terminal. i don't have a problem with the graphic interface, but the terminal is foreign to me

---

### Post by aysiu on 2006-07-16
We'll take it one step at a time, then.

I think the first thing you should do is print out the entire link I just gave you. Print it out on a piece of paper you can physically hold in your hands.

Then, reboot. When you reboot, if you're dual-booting, the second option you see should be called **Recovery Mode**. If you're single-booting, you may have to press Escape during boot-up to see the Grub menu and select **Recovery Mode**.

Once you're in **Recovery Mode**, you will have root privileges. The page I linked to will give you specific commands to enter into the terminal, but the general gist is that you want to make sure your username is in the *admin* group in the /etc/group file.

---

### Post by Zingomoos135 on 2006-07-16
i can't print from my linux box, so i just wrote down the backup and edit commands. is that enough?

---

### Post by aysiu on 2006-07-16
Should be enough. Just keep in mind that everything in the terminal is case-sensitive. Any one typo will give you errors.

Best of luck. I've got my fingers crossed for you.

---

### Post by Zingomoos135 on 2006-07-16
that worked PERFECTLY! thank you SO MUCH for your assistance!!!!:KS :KS :KS

---

