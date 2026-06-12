---
title: "Natty Ubuntu Classic maximise issues"
date: 2011-04-29
forum: Desktop Environments
---

### Post by monkey21stc on 2011-04-29
Hi all,

I am using Ubuntu 11.04 Classic Desktop, I have unchecked the Unity Plugin from CCSM to revert to the original desktop as Unity was running too slowly on my netbook. However whenever I maximise a window, I get this: *(see attached)*. I am not sure what is causing this, I am using maximus and window title applet and window buttons applet. Switching window manager from compiz to metacity did solve the issue, but it resulted in gnome-panel to crash. When I open up system monitor, I noticed unity-window-decorator running. Killing the process removed the window decorators and I managed to maximise without any issues. 

Is there anyway where I am able to switch the windows decorator to the one in 10.10? or perhaps an alternative solution for this issue? Thank you!

---

### Post by Krytarik on 2011-04-30
Check the setting "CompizConfig Settings Manager -> Window Decoration -> Command", the default value is "/usr/bin/compiz-decorator".

Hope it helps!

---

### Post by luke-alike on 2011-05-08
> **Krytarik said:**
> Check the setting "CompizConfig Settings Manager -> Window Decoration -> Command", the default value is "/usr/bin/compiz-decorator".

Hope it helps!


I set the value to **"/usr/bin/maximus"** in Compiz - rebooted PC - **SOLVED!**

---

