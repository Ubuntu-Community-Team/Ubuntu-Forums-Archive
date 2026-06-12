---
title: "nautilus won't respect --geometry"
date: 2006-07-17
forum: Desktop Environments
---

### Post by vayu on 2006-07-17
I'm trying to get nautilus to open a file browser window of a specific size and location.  According to man and a few pages I should be able to do that with the --geometry option.

I'm trying

nautilus --no-desktop --geometry=640x480+50+50

But it insists on opening the same size window as the last time I closed a nautilus window.

Maybe it's a compiz issue, anybody know?

---

### Post by philippe_carlo on 2006-07-17
Nope, not compiz. Seems to be broken here too (not using compiz). It must be a bug!

---

### Post by vayu on 2006-07-17
> **philippe_carlo said:**
> Nope, not compiz. Seems to be broken here too (not using compiz). It must be a bug!

I just realized it shouldn't be compiz because it works fine for gnome-terminal on my system.

Anyone have this working, what format do you use to specify the window size and position?

---

### Post by philippe_carlo on 2006-07-17
I used the documented one, which you can find all over the internet. I.e., the one you proposed. XxY+X+Y

---

### Post by tonywhelan on 2007-10-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/154594](https://bugs.launchpad.net/bugs/154594) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **vayu said:**
> I'm trying to get nautilus to open a file browser window of a specific size and location.  According to man and a few pages I should be able to do that with the --geometry option.

I'm trying

nautilus --no-desktop --geometry=640x480+50+50

But it insists on opening the same size window as the last time I closed a nautilus window.

Maybe it's a compiz issue, anybody know?

Just found this thread after a search looking for some decent info about the geometry argument, because I too wanted to be able to open Nautilus windows of a set size and position. Pity the bleeding "man" page doesn't tell us what the format of the geometry arguments should be. 

In Gutsy (gnome 2.20) I had the same problem as reported above, but only if the last Nautilus window was maximised. If I resize a Nautilus window to less-than-maximum, close it, then run the nautilus --no-desktop --geometry=640x480+50+50 command, it works fine for me.


I reported this as a bug this week.

---

