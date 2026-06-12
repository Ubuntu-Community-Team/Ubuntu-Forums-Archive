---
title: "missing launcher and/or menu bars"
date: 2011-10-17
forum: Desktop Environments
---

### Post by F104G on 2011-10-17
Well... Ubuntu just upgraded to 11.10 and I have the new Unity desktop.  Tried making the "Launcher" (sorry: not sure of it's proper name - the panel on the left that contains icons for Home, Firefox, Software Centre etc.) smaller in Compizconfig and it made the top menu bar on all windows disappear.  Looked for a solution online and tried Metacity --replace in Terminal.  This got me my menu bar back but got rid of the launcher.  Also: no top panel where the on/off icon lives, so no way to log out/back in again.  Had to turn off comp by holding down the power button.  On restart, everything looks fine but the launcher is back to it's original HUGE size.  Tried it in 2D and it works OK but changing the size of the launcher has no effect.
All I want is a smaller launcher - what am I doing wrong, huh? :confused:

---

### Post by GarbloJones on 2011-10-17
make sure that you don't mess too much with unity --- it can be finicky when you're trying to reintegrate it.

rather, try to work around / with it.

i'm sure you know you have to change the icon sizes in compizconfig ... but did you realize you have to do a full restart before the changes take place? 

even though i hardly use the sidebar (i prefer cairo dock cause of better customization), i have it set to the lowest icon size and it doesn't look too ridiculous.

i dunno if it'll help but this thread i started a couple of days ago might provide some useful info.

[http://ubuntuforums.org/showthread.php?t=1861523](http://ubuntuforums.org/showthread.php?t=1861523)

---

### Post by F104G on 2011-10-18
Hmmm...

a complete close-down and re-start gets me back to square one, i.e. a small launcher bar (looks OK) but no top menu bars, so I am unable to minimise/maximise or drag windows around.  If I try metacity --replace in Terminal the launcher and the top panel disappear - and I have to crash-out by holding down the power button.

I have tried to fiddle around as little as possible :-\"
Thanks for your help so far.

---

### Post by kriegoamigo on 2011-10-18
:|

---

### Post by F104G on 2011-10-18
> **kriegoamigo said:**
> :|

Indeed!

I have (temporarily?) gone back to Gnome while I look for an answer to this.  It seems the update has affected that one too, as the top panel is a shade lighter behind the menus Applications & Places and the clock etc.  makes it look a bit clunky.  And I'm unable to move things around up there with a right-click.  Anyroadup... it'll do until I can figure-out what the deal is with Unity.

Anyone?

---

### Post by libertao on 2011-10-20
Try ctrl+alt+t to bring up terminal, type ccsm, then enter, then go to Desktop option on the left, then enable Unity plugin (hopefully that was not enabled).  I selected "resolve conflicts" and selected every following one in favor of Unity.  Immediately brought back the launcher.

---

### Post by tim290280 on 2011-10-22
> **libertao said:**
> Try ctrl+alt+t to bring up terminal, type ccsm, then enter, then go to Desktop option on the left, then enable Unity plugin (hopefully that was not enabled).  I selected "resolve conflicts" and selected every following one in favor of Unity.  Immediately brought back the launcher.
Thanks for that quick link. Accessing everything was a bitch without terminal or menus.

---

### Post by fariposter on 2011-11-11
> **libertao said:**
> Try ctrl+alt+t to bring up terminal, type ccsm, then enter, then go to Desktop option on the left, then enable Unity plugin (hopefully that was not enabled).  I selected "resolve conflicts" and selected every following one in favor of Unity.  Immediately brought back the launcher.
Saved my life!

---

