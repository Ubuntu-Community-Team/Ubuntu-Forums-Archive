---
title: "Compiz and window selection"
date: 2018-04-16
forum: Desktop Environments
---

### Post by kregg2 on 2018-04-16
Hey all,

I installed Compiz onto Xubuntu, and have a single problem with it;

When I select a window from the panel, the window is not automatically 'selected'.

This means if I maximise the window, and want to minimise it again, I have to click three times on the panel; once to maximise, another to 'select' the window, and then once more to minimise it again.

Has anyone had this issue, and then solved it?

Any help is much appreciated!

Cheers!

---

### Post by #&amp;thj^% on 2018-04-16
> **kregg2 said:**
> Hey all,

I installed Compiz onto Xubuntu, and have a single problem with it;

When I select a window from the panel, the window is not automatically 'selected'.

This means if I maximise the window, and want to minimise it again, I have to click three times on the panel; once to maximise, another to 'select' the window, and then once more to minimise it again.

Has anyone had this issue, and then solved it?

Any help is much appreciated!

Cheers!
You may have to play with the setting's in CCSM.
So open CCSM and go to >>>General,click that and on the right you will see Tabs at the top, select Focus & Raise Behaviour and set it to "low" or even better yet set it to Off or None.

---

### Post by kregg2 on 2018-04-16
Hey thanks for the reply!

I tried the fix you mentioned, but the behaviour is still the same :(

I will have a mess around with the other settings and see what happens.

Is there a config I could edit maybe?

---

### Post by #&amp;thj^% on 2018-04-16
This only happens when clicking a open window from the panel right?

---

### Post by kregg2 on 2018-04-16
Yes.

I have just tested and noticed that some programs such as Firefox and Thunar don't have this problem. 

Others, like VLC for example, do have the problem.

I am stuck :confused:

---

### Post by #&amp;thj^% on 2018-04-16
I'm just not seeing that here. :( Makes it hard for me to help you when i can't produce the same as you see.
What version of Xubuntu are you using:
```
lsb_release -a
```

---

### Post by kregg2 on 2018-04-16
Its 16.04.4 LTS

I did have to mess with dconf to get the window theme working, but all I did was change the default to Numix.

When I switch back to xfwm4, the problem disappears.

I didn't have this problem on a previous machine, and as I say its not consistent.

At first I thought that maybe it was only happening on programs installed after installation, rather than programs that came with the OS. But gnome-disks is working fine. 

All other programs installed that weren't packaged with the OS have the problem.

---

