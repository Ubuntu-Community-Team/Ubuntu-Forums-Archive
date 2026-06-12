---
title: "Applications don't dock in gnome panel"
date: 2005-02-17
forum: Desktop Environments
---

### Post by Estariel on 2005-02-17
Hi!
I'm new to Ubuntu, and I'm new to gnome too.

I have been using KDE on top of Gentoo for the last two years; but lately it has been feeling too unstable for my taste (since I have to get some serious work done)

Thus I thought I'd give Ubuntu a try.

Now I have the following problem:

If I launch an application, it sometimes won't show up in the task bar (gnome panel), so if i minimize the window it is gone and i can't get it back.

Most of the time this happens with evolution. I think evolution only docks into the task bar in one of three times I start it.

Nautilus shows the same behaviour (although it docks far more often)

The only application that _always_ docks into the panel is firefox.


So what's going on here? I simply don't understand this...

Thanks for help!

Estariel

---

### Post by Estariel on 2005-02-17
ok, i figured it out: I am running in xinerama mode (dual monitor setup with nvidias TwinView).

The GnomePanel is on my left screen.
All Applications on my right screen don't show up in the panel. if i drag them to the left screen, they suddenly show up. If I drag the panel to the right screen, all applications on the left screen vanish from the panel, and all on the right screen show up.

I've been looking for a solution for half an hour now... how do I change that behaviour?!

Please help me, this is driving me nuts...

Estariel

---

### Post by Buffalo Soldier on 2005-02-17
Which version are you using (Warty or Hoary)? Is the Window List applet running?

---

### Post by Estariel on 2005-02-17
I'm on Warty

The Window List applet is running (in the Panel on the left screen)

I created a second panel and placed it on the right screen, added a windowlist applet to it and that kind of fixed the problem (though i still only get the windows on the right screen on the right screen panel, and vice versa)

Thanks for your help :)

---

### Post by Mindstab on 2005-02-19
I had/have this problem.
I had it with gentoo. I think it has something to do with some component libwnc or something
I downgraded and it went away. Ideally someone noticed this and filed a bug and when hoary comes out it will be fixed :)

---

