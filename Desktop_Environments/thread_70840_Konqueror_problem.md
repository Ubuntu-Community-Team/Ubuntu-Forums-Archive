---
title: "Konqueror problem"
date: 2005-10-01
forum: Desktop Environments
---

### Post by Freddy on 2005-10-01
I have a little problem with konqueror. I compiled and installed the new "stable" version of the maclike theme Baghira and my sidebar vanished, I would like to have the one that came with Baghira but to be able to use that plugin I must get my sidebar back. Now it seems that I'm using the web style for konqueror at all time.

How to get it back ?   /// Freddan

---

### Post by Sirin on 2005-10-01
[QUOTE=Freddy]I have a little problem with konqueror. I compiled and installed the new "stable" version of the maclike theme Baghira and my sidebar vanished, I would like to have the one that came with Baghira but to be able to use that plugin I must get my sidebar back. Now it seems that I'm using the web style for konqueror at all time.
How to get it back ?   /// Freddan[/QUOTE]
Press F9 while Konqueror is open. :)

---

### Post by Freddy on 2005-10-01
[QUOTE=Sirin]Press F9 while Konqueror is open. :)[/QUOTE]
Thank's dude, didn't know that :).   /// Freddan

---

### Post by Freddy on 2005-10-01
Hey again, I have another problem for your konqueror skills, by altering the ~/.kde/share/config/konqsidebartng.rc and put a true after the "hide konqueror sidebar" option, I have done this before but that file seems screwed now. I had no such option left and I'm stuck with the buttons at the right side of the sidebar.

What to do ?   /// Freddan

---

### Post by Sirin on 2005-10-01
[QUOTE=Freddy]Hey again, I have another problem for your konqueror skills, by altering the ~/.kde/share/config/konqsidebartng.rc and put a true after the "hide konqueror sidebar" option, I have done this before but that file seems screwed now. I had no such option left and I'm stuck with the buttons at the right side of the sidebar.
What to do ?   /// Freddan[/QUOTE]

Hmm... Never had this problem before... Have you tried reinstalling Konqueror via Synaptic?

---

### Post by Freddy on 2005-10-01
Well that won't work, cause all the config files are kept. Maybe if I deleted mine for the sidebar and attempted a reinstall. 

Can someone post their /home/freddan/.kde/share/config/konqsidebartng.rc and I will attempt to modify the one I have, thanks in beforehand.   /// Freddan

---

### Post by Knome_fan on 2005-10-01
```
[$Version]
update_info=konqsidebartng.upd:konqsidebartng_rc

```

That's all there is in mine.
But I think you could just delete this file, or rename it and then restart kde to fix your problem.

---

### Post by Freddy on 2005-10-01
[QUOTE=Knome_fan]```
[$Version]
update_info=konqsidebartng.upd:konqsidebartng_rc

```
That's all there is in mine.
But I think you could just delete this file, or rename it and then restart kde to fix your problem.[/QUOTE]
I already tried that and it didn't work it just created a file that looked the same as before. I pasted your line to my file and it seems to be fixed now, thanks.   /// Freddan

---

