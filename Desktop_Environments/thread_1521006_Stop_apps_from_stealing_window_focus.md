---
title: "Stop apps from stealing window focus?"
date: 2010-06-30
forum: Desktop Environments
---

### Post by whein on 2010-06-30
I have found a couple of posts complaining about this problem but none offering solutions.  In a nutshell, I want to prevent ALL programs from creating new windows that steal the keyboard focus away from whatever window I was just using.  The most common offender is Synaptic when running updates/installs.  I will be typing an email, playing a game, whatever, and all of a sudden a new window will pop up, steal focus, and if I'm not paying enough attention, whatever I'm typing will interact with it and cancel something or say yes to something before I even realize it.  Another really bad offender is Firefox with the dialogs to accept cookies or entering/leaving a secure website.  I still want all of those dialog boxes to appear but I don't want them to automatically steal focus from my other applications.  Another user suggested having them blink in the task bar and I like that well enough if it is possible.

Is there a way to lock the focus to the active program/window unless the end user switches it away (i.e. no stealing)?

One post said something about window rules but gave no details.  A lot of posts talk about the mouse cursor position selecting the window option (which I do not want and would not fix this problem anyway).  One post said it was fixed in Feisty (guess it came back...)  And none of th posts seem to give instruction for fixing it.

Help?

-Will

---

### Post by ClyN3il on 2010-12-27
Here here! What's the solution to this? This has been a problem in every OS and on every desktop environment/window manager I've used recently...and it's so annoying! I can barely type a complete sentence without having to switch back to the window I was typing in at least once. Maybe it's because I'm a compulsive multitasker and typically have at least a dozen apps running... But I'd appreciate it if nothing is allowed to steal my focus, ever. How hard could that be?

Ok, since I'm using Compiz, I went to the Focus & Raise Behaviour tab in general options and changed Focus Prevention Level from Low to Very High. Let's see if this helps. And I think I just lost my focus. Maybe if I restart Compiz? ...

---

### Post by reedlaw on 2011-03-08
I am having the same problem. Anybody have a solution for this? In my Compiz Focus & Raise Behavior, Focus Prevention Windows I have:

```
!(class=Polkit-gnome-authentication-agent-1) !(class=Firefox)
```

---

### Post by svenskmand on 2011-06-29
Bump

---

### Post by superfrank on 2011-08-19
Yeah this issue causes so many problems for me.

I think a sensible solution that should apply to every single OS ever made would be never allow the focus to be changed by another application when there has been keyboard activity within the last two seconds.

---

