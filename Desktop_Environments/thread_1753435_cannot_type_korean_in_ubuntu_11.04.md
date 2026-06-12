---
title: "cannot type korean in ubuntu 11.04"
date: 2011-05-09
forum: Desktop Environments
---

### Post by jesse.au on 2011-05-09
I have been having multiple problems setting up my friends computer to type korean. I installed *Smart Common Input Method* but none of the hot keys seem to register. If you need more info about the computer or installation just ask!

---

### Post by grummbaleena on 2011-05-25
I just set this up on 11.04, but an important note is that I'm using the gnome desktop instead of unity.

First go to System -> Administration -> Language Support -> Install / Remove Languages, scroll down to Korean, and under Components ensure that Input methods and Extra fonts are selected. Then hit Apply Changes. After any required packages are finished installing, change the Keyboard input method system to ibus by selecting from the dropdown menu. To start the ibus keyboard input method go to System -> Preferences -> Keyboard Input Methods. You should be prompted with a message to start the ibus daemon, after which you should see the ibus applet sitting in the top right near the other indicators. From the IBus preferences you can configure it's behaviour as you like. Under the Input Method tab you can add the Korean input method and under General you can setup the preferred keyboard shortcuts.

Hopefully this info is useful in some way, I didn't really use Unity at all, first thing I did when I installed Natty was switch to gnome. I remember having problems in the past with SCIM and much prefer ibus for managing keyboard input.

---

