---
title: "Some Problems With KDE In 11.10"
date: 2011-10-13
forum: Desktop Environments
---

### Post by dniMretsaM on 2011-10-13
Problem 1: All windows launch without any title bars. I've looked in System Settings -> Workspace Appearance -> Configure Decoration... -> Window-Specific Overrides to see if an exception had been made to keep title bars from showing up, but everything is normal. Also, some problems that (I assume) are related are that I can't minimize/maximize windows and I can't move them around (Alt-click).

Problem 2: When any application is open, all menus (except when you right click on a panel or widget) disappear when you touch them with the mouse. So if I have Firefox open and I click on Kickoff, it will appear on the screen as it should. However, when I my cursor touches the menu, it disappears.

Any suggestions one how to fix these? And the quicker the better. It's very hard to use the system like this.

By the way this is a fresh install. Burnt the CD at 10x average, verified the data, and checked the CD for errors before installation.

Filed [bug #873790](https://bugs.launchpad.net/ubuntu/+bug/873790).

---

### Post by 23dornot23d on 2011-10-13
Have you tried CCSM compiz settings manager

its possibly borders and movement controls .... for windows ....

I had it happen not so long back ..... using the arrow keys up and down
will let you select things in the menus as it stands ....

But to fix it you need to use CCSM

---

### Post by dniMretsaM on 2011-10-13
> **23dornot23d said:**
> Have you tried CCSM compiz settings manager

its possibly borders and movement controls .... for windows ....

I had it happen not so long back ..... using the arrow keys up and down
will let you select things in the menus as it stands ....

But to fix it you need to use CCSM

I'm using the Kwin window manager, not Compiz. Also, I know about using arrow keys for menu navigation. It works, but it's a little annoying sometimes.

EDIT: Filed a bug report: [Bug #873790](https://bugs.launchpad.net/ubuntu/+bug/873790)

---

### Post by sumski on 2011-10-14
Have you tried deleting kwinrc and kwinrulesrc?

---

### Post by dniMretsaM on 2011-10-14
> **sumski said:**
> Have you tried deleting kwinrc and kwinrulesrc?

Yep, tried that but it didn't change anything.

---

### Post by samigina on 2011-10-14
Safe mode session works? It looks like a driver issue.

---

### Post by dniMretsaM on 2011-10-14
> **samigina said:**
> Safe mode session works? It looks like a driver issue.

I didn't think of it being a driver issue. I have 9 year old hardware, so it's usually pretty well supported. I'll check safe mode and report back.

---

### Post by dniMretsaM on 2011-10-14
Booted to GRUB -> Recovery mode -> Resume normal boot (I assume this is safemode) and everything looks the way it should (except for everything on the screen being huge, but that's safe mode for ya').

Here's the video line from [FONT=Courier New]lspci[/FONT]:
```
VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
```

---

### Post by dniMretsaM on 2011-10-14
Solved! I changed the compositing type from OpenGL to XRender and that fixed all my problems. Well, all my computer problems that is.

---

### Post by german_ch90 on 2011-10-15
> **dniMretsaM said:**
> ... and that fixed all my problems. Well, all my computer problems that is.

Haha I loved that last thing you said, lucky you I still haven't figured out my KDE related problems that came with my recent 11.04->11.10 upgrade. :(

---

### Post by dniMretsaM on 2011-10-16
> **german_ch90 said:**
> Haha I loved that last thing you said, lucky you I still haven't figured out my KDE related problems that came with my recent 11.04->11.10 upgrade. :(

Lol thanks. Create a new thread about it. I'm sure someone on the forum will be able to help you out (PM me with a link to it when you post, I'll see if I can help).

---

