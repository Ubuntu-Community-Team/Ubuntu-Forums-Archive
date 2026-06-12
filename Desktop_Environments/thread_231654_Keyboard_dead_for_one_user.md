---
title: "Keyboard dead for one user"
date: 2006-08-07
forum: Desktop Environments
---

### Post by steevc on 2006-08-07
When my wife logs onto our PC she sometimes finds that the keyboard is totally dead, i.e. even the Caps/Num lock lights don't work. Saw this today when I was logged in too. My session was fine. Eventually we got locked out of her session and couldn't type the password to get back in. Managed to reproduce it a couple more times.

The keyboard is an old PS/2 type.

Any ideas?

---

### Post by der_joachim on 2006-08-08
I had the same issues a few times in KDM. You can still use the mouse though. Firing up the console login and restarting kdm solved the problem. I do not know which desktop manager you use, so I could be totally wrong.

---

### Post by steevc on 2006-08-09
I'm using KDE as I installed Kubuntu. Last night I had 3 sessions running. Two were fine, but my wife's had the dead keyboard again. It looks like something is messed up with her settings. I could be tempted to wipe her /home and start again if I don't find a solution. I just don't know where I should be looking.

Thanks

---

### Post by steevc on 2006-08-10
Problem solved! Somehow Slow Keys had got turned on, so you had to hold a key down for a while before it did anything. Now she tells me that something about that had popped up. I need to check up on that. I think it might happen if you accidentally hold a key down for too long, but I'm not at the Linux box just now.

---

### Post by coquinho61 on 2008-01-31
True. See [here]("http://ubuntuforums.org/showthread.php?t=458036&highlight=kde+lost+keyboard") for a good explanation plus solution.

---

