---
title: "&quot;Disable touchpad while typing&quot; does not work in Xubuntu 20.04"
date: 2020-10-14
forum: Desktop Environments
---

### Post by ccrs8 on 2020-10-14
On my laptop running Xubuntu 20.04, the "Disable touchpad while typing" setting does not work.  Regardless of what I have it set to, my touchpad is never disabled when I'm typing.  It's infuriating, as I'm constantly accidentally relocating my mouse pointer while typing, accidentally changing my typing location and sometimes even accidentally highlighting and deleting large amounts of text.  Other settings found in the "Mouse and Touchpad" settings screen work fine ("Tap touchpad to click" for instance), just not the setting to disable touchpad while typing.  I've resorted to making sure I always have a wireless mouse with me so that I can disable the touchpad altogether, and failing that I disable the "tap to click" option so that I'm not accidentally clicking while typing - which makes the touchpad much less useful.

I have tried with an Xubuntu 20.04 LiveUSB session and it still does not work.  However, in a live session of Pop!_OS 20.04 it works perfectly.  And I know it's not something generally wrong with Xubuntu because my wife's laptop (a Dell XPS) also has Xubuntu 20.04 and the setting works as expected, so it's something specific with my laptop.  My laptop is a System 76 Lemur Pro purchased earlier this year, so it's never had an earlier version of Xubuntu on it.  The setting worked perfectly in earlier versions of Xubuntu on my older Lemur Ultra System 76 laptop.

Any ideas?

---

### Post by ajgreeny on 2020-10-14
What's the terminal output of ```
synclient -l
```which may give us a few clues.

---

### Post by ccrs8 on 2020-10-14
> **ajgreeny said:**
> What's the terminal output of ```
synclient -l
```which may give us a few clues.

I actually just fixed my problem.  I noticed when running the command that TouchpadOff = 1 was in the output, which was strange because the touchpad was definitely working.  I went to google "touchpadoff" in order to make sure I understood what Touchpadoff meant, and the search bar autocompleted to "synclient touchpadoff=1 doesn't work" and the very first hit on that was this post which described my exact problem and the fix fixed my issue completely:
[https://forums.linuxmint.com/viewtopic.php?t=229932](https://forums.linuxmint.com/viewtopic.php?t=229932)

I should have mentioned in my initial post that I had two touchpads show up in my settings, but nothing on the PS/2 entry ever did anything so I just ignored it.  Anyway - I'm all set and thanks @ajgreeny for the hint.

---

