---
title: "KDE: Control panel empty!"
date: 2008-02-19
forum: Desktop Environments
---

### Post by johann_p on 2008-02-19
Using Ubuntu Gutsy 32bit with both GNOME and KDE installed.
I had been using GNOME for some time now and wanted to use KDE again. When I run kcontrol, all I get is a nearly empty window: the only category in the left bar is "Network" and when I click that, it is empty!

What happened to the control center :confused:

How is one supposed to change all the settings that can be changed in KDE?

---

### Post by aysiu on 2008-02-19
Does this happen for all users on your computer, or only the one you use?

Hint: if you have only one user, create a new test user.

---

### Post by johann_p on 2008-02-20
> **aysiu said:**
> Does this happen for all users on your computer, or only the one you use?

Hint: if you have only one user, create a new test user.

I created a test user and found the same situation there.

---

### Post by johann_p on 2008-02-21
Does anyone else have this problem too? Any ideas how I could solve this?

---

### Post by GeneralZod on 2008-02-21
I've not seen this before (although I once saw an app that had all its settings missing).  The only thing I can think of is that kcontrol isn't picking up the kcm_shells.   Running

```

kbuildsycoca --noincremental

```

from the command-line might help.

---

### Post by johann_p on 2008-02-21
> **GeneralZod said:**
> I've not seen this before (although I once saw an app that had all its settings missing).  The only thing I can think of is that kcontrol isn't picking up the kcm_shells.   Running

```

kbuildsycoca --noincremental

```from the command-line might help.
Unfortunately running this did not change anything :(

---

### Post by johann_p on 2008-03-12
My control panel is still empty? 

Any ideas what could be the reason? Is this a known bug?

---

### Post by fatagnus on 2008-03-14
The same thing happens to me, I tried running kcontrol from the console, and got this output:

```

qstring_to_xtp result code -2
kcontrol: WARNING: No K menu group with X-KDE-BaseGroup=settings found ! Defaulting to Settings/

```

Although I don't know what I can do to repair this, except reinstall from synaptic, wich I already done with no results.

---

### Post by Naneau on 2008-03-30
I would like to report the same issue, I too get the same

```
kcontrol: WARNING: No K menu group with X-KDE-BaseGroup=settings found ! Defaulting to Settings/
```

I installed ubuntu gutsy, and just installed the "kde" package afterwards, I did *not* install kubuntu-desktop (seeing as how I want gnome/ubuntu to remain my default environment)

---

### Post by johann_p on 2008-04-12
I find it a bit odd and hard to believe that this is something that is obviously not extremely rare, something that is extremely annoying -- not just a minor glitch  and there does not seem any solution around anywhere.

---

