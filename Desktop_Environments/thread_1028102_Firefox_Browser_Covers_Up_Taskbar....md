---
title: "Firefox Browser Covers Up Taskbar..."
date: 2009-01-02
forum: Desktop Environments
---

### Post by Gunmetal_Ghoul on 2009-01-02
When I go to the Firefox browser it takes up the space where the taskbar usually is. It just cuts off above the menu and doesn't show the header or the browser's icons for exit, minimize and resize. They are just plain missing and I have to press CTRL+Q to exit. I may not know why it's covered up but I discovered when I turn off the visual effects it goes back to normal. I wanna have my desktop effects:(....

---

### Post by Sin@Sin-Sacrifice on 2009-01-02
Open firefox, click anywhere on it (except a link or file browser or something) then hit F11. Should bring it back to normal. If it doesn't work then try clicking another spot on firefox and then F11 again.

---

### Post by zika on 2009-01-02
F11-F11-Unmaximize->Resize window to something well within visible screen->Maximize, if You want->enjoy ...

---

### Post by Sir_Sid on 2009-01-13
Is there a bugreport for this?

---

### Post by 11lettenJ on 2009-01-13
This very briefly happened to me and I had to get around it by immediately hitting F11 twice. It seems to have gone away though after a reboot

---

### Post by arm-c on 2009-01-13
I had problems similar to this.  

The result was using some sites that would maximize the browser through some sort of code in page.

To the user... if a window is off the screen, hold down the control key and click anywhere on window you want move and drag it.  Great feature I miss when using windows. :)

After you have opened firefox.  Resize the window to fit in your screen area and then close / exit it.  After you start again, you should be back to normal.  I personally think it is a bug in firefox.

Well, that should do it.  Hope helps.  :)

Oh, I say this because I would try the F11 thing a few times... didn't work for me in long run.  I would notice that when I was stuck in this, it was indicated by the title bar not getting focus in effects until I minimized and restored (Opened / FF opened full screen / F11 / No focus on title bar even if window had focus / min/restore fixed focus.)  The above worked for me.

---

### Post by zika on 2009-01-14
System->Preferences->CompizConfig_Settings_Manager->Utility->Workarounds->**uncheck**_Legacy_FullScreen_Support

---

### Post by cb34 on 2009-01-14
in firefox options up top.. find javascript, go into options for it, i usually shut all that stuff off, i dont want some website to be able to resize my windows.. also.. ive had the same problem as you, and i had to turn off and on compiz to fix it.. it was the window manager that something got screwed up for the moment.. check any settings on any new themes or something you may have installed/tweaked ..

---

### Post by zika on 2009-01-14
> **cb34 said:**
> in firefox options up top.. find javascript, go into options for it, i usually shut all that stuff off, i dont want some website to be able to resize my windows.. also.. ive had the same problem as you, and i had to turn off and on compiz to fix it.. it was the window manager that something got screwed up for the moment.. check any settings on any new themes or something you may have installed/tweaked ..
with a fix I gave in a previous post You don't have to toggle compiz and java. try it.

**in metacity** Alt-F2->gconf-editor->apps->metacity->general->(un)check_disable_workarounds
**in compiz **System->Preferences->CompizConfig_Settings_Manager->Utility->Workarounds->**uncheck**_Legacy_FullScreen_Support

---

### Post by cb34 on 2009-01-14
give up on java and compiz????

i just shut off, then turned it back on.. basically restarted compiz..
and disabling those javascript options does not disable java or javascript.
i know you probably know this, just maybe you misunderstood my post.

---

### Post by zika on 2009-01-14
I've corrected my statement ... ;) (just in the part about compiz and java. in the fix part I stand solid ... ;)) (I use minefield lately so that is the third fix ... ;))

---

