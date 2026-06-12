---
title: "I want to disable screen blanking while I'm watching a movie"
date: 2023-03-14
forum: Desktop Environments
---

### Post by jbayes2 on 2023-03-14
I'm running an up-to-date install of xubuntu 22.04 on a desktop hooked up to my TV.
When I start up a browser, go to netflix.com, start a movie, and put it in fullscreen mode, it works fine for about five minutes and then the screen goes blank. 
I can temporarily re-awaken the screen if I jiggle the mouse, but it goes blank again five minutes later. 

settings->screensaver-> Inhibit screensaver for fullscreen applications is ON
->enable screensaver is OFF
->lock screen -> enable lock screen is OFF
In settings->power manager->system, the "when inactive for" slider is set to NEVER
settings->power manager->display->display power management is set to OFF and all 3 sliders are set to NEVER

How do I keep the screen on while watching a movie?

I'm happy to respond with any diagnostic data you need.

Thanks!

ETA: screen also blanks when I don't have a fullscreen program running.

---

### Post by Holger_Gehrke on 2023-03-14
Is this on a laptop or a desktop ? On my laptop the power management options exist twice, once for the system running on battery and once for the system running on external power. Also, if you allow the power manager to have an icon in the status area you can click on that and choose presentation mode which disables all screen blanking until you switch presentation mode off again.

Holger

---

### Post by bobunderwood99 on 2023-03-14
Have you tried enabling Presentation mode? Click the Power Manager Plugin (battery icon by the clock).

Ahh,  ninja'd by HG.

---

### Post by jbayes2 on 2023-03-14
On a desktop. 
When I open the power manager and enable the system tray icon, the system tray flickers but no persistent icon appears. 
(edit: I right-clicked on the panel, went to panel->add new items, and added a power management plugin. Turned on presentation mode, waiting to see if that fixes the problem.)

But since display power management is off entirely, I wonder if maybe it's some other program doing the screen blanking?

---

### Post by ajgreeny on 2023-03-14
As you're using Xubuntu you are in luck.
If you click on the **power-manager-plugin** or **battery** icon in your panel you will see a dialogue pop up (see screenshot) with **Presentation mode** selection switch offered.  Choose that and the screensaver if used or all other screen power-manager options are disabled and the display stays alive.

There may be other ways to do this but it's what I've used many times and is quick and easy to enable or disable.

---

### Post by jbayes2 on 2023-03-14
Okay, adding the power manager icon and switching to presentation mode worked. Thank you!

---

### Post by ajgreeny on 2023-03-15
Great!

Please now mark as SOLVED from the Thread Tools menu up top; it's a great help to others using the forum.

---

