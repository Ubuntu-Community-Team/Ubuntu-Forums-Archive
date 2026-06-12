---
title: "[SOLVED] Compiz slow after restart (was fast at installation)"
date: 2008-01-19
forum: Desktop Effects &amp; Customization
---

### Post by jaredssix on 2008-01-19
(Sorry, this is repost from absolute beginners--but I wasn't getting any responses!)

Hey all,
I just installed compiz and launched the cube, wobblies, etc.
Everything was super clean and fast until I restarted, and now all the graphics are slow--even typing is slow!

What did the restart miss?

I should mention that the cube is fast; the windows effects are slow.

My card is intel 915, which I would guess is rather minimal--but everything looked so good until the restart!

--Jared

---

### Post by Ub1476 on 2008-01-19
Have you been installing any updates lately? Make sure that backports is not enabled in software sources either.

---

### Post by jaredssix on 2008-01-19
No new updates.

How do I disable backports in software sources?

---

### Post by Ub1476 on 2008-01-19
Sorry, I meant_ not_ enabled (you find it in software-sources). Also, I didn't ask whether there were any new updates, but previous which might have caused issues;)

You can also try to revert your compiz settings in CCSM>Preferences.

---

### Post by jaredssix on 2008-01-19
Thanks for the help through this . . .
I went to software sources, and saw no mention of backports--so I figure they're disabled . . ?

And no updates that would have had any effect on the graphics. I installed the compiz package last night, and everything was smooth and fluid. 

When I awoke and restarted my system, the cube is still in effect, but the graphics are choppy.

It all happened so fast!

---

### Post by Ub1476 on 2008-01-19
Backports is located in Software-sources>Updates>Ubuntru updates (uncheck).

To clean all your settings open CCSM (advanced desktrop..)>Preferences>Reset to defaults.

Restart and see if anything has changed.

---

### Post by jaredssix on 2008-01-19
So, all four of the update boxes are unchecked under software-sources>Updates>Ubuntru updates.

I reset CCSM to defaults, restarted, and lost the cube!

I entered "compiz" into the terminal, but still no cube. 

Ideas?

---

### Post by Ub1476 on 2008-01-19
Yes you lost the cube because it is not enabled by default:p

Just check it in CCSM.

BTW, **gutsy-security** and **gutsy-updates** is supposed to be enabled.

---

### Post by gspat on 2008-01-19
try enabling desktop effects to normal - this should reset some of the settings to default and get things working again.

---

### Post by jaredssix on 2008-01-19
Thanks everyone,
It appears all is well after a complete uninstall, reinstall--even the fast and fluid bit which started all this (4 hrs ago)!

Update manager may have a few things to add.

Also, set transparent cube opacities to 100--the littlest bit of opacity slows things down a lot.

---

