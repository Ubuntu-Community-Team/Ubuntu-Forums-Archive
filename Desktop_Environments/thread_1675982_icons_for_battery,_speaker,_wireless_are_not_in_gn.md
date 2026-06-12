---
title: "icons for battery, speaker, wireless are not in gnome panel"
date: 2011-01-26
forum: Desktop Environments
---

### Post by zehra on 2011-01-26
I have been using Ubuntu without any problem for 2 years. Yesterday, when I booted Ubuntu, its power management is not working at start up:**[COLOR=Black] icons for battery, speaker, wireless not there[/COLOR]** + light icon says "**cannot connect to gnome-power-manager**".( in the screenshot) 

When I go System - Preferences - Power Management (1), it corrects only the light icon.

I could only bring back wireless icon by "nm-applet" after doing (1).But other icons are not there still.

Any help is appreciated..

---

### Post by Frogs Hair on 2011-01-26
This will reset the panel to defaults , but I don't the cause of the problem. Welcome to the forums
```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by zehra on 2011-01-27
Thanks for your reply,

I tried the code, still when I booted Ubuntu none of icons and functionalities are available. 
But improvement is in battery icon: opening System - Preferences - Power Management brings battery icon back, and corrects brightness functionality.
I still need to call "nm-applet" to use wireless.

Interestingly I also realized that I cannot mount VistaOS anymore. When I click VistaOS from Places menu, it says "Unable to mount VistaOS- Authentication is required". 

Can these errors be related?

---

### Post by zehra on 2011-01-27
I suspect that all errors might have happened because Startup Applications are not started somehow, although all are ticked. 

I have this thought because
- I copied command under "Volume Control" into terminal and hit return, and volume control applet became visible in gnome desktop panel.
- I run command under "PolicyKit Authentication Agent" in terminal , then a key icon became visible, and now clicking Places- VistaOS triggered asking for password, then  opening VistaOS folders, as it should.

However, I have to run all these commands in separate terminals in each startup. 
How can I handle this?

Thanks in advance..

---

### Post by zehra on 2011-01-27
I found the solution:

> **Jawshie said:**
> Nevermind, I solved it.

On the login page at the bottom is a panel. On it, somehow the "Safe  Mode" choice was selected for desktop environment. I changed it back to  the regular Ubuntu choice and it works.

---

