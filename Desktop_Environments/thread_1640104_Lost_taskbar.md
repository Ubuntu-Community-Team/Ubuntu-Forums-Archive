---
title: "Lost taskbar"
date: 2010-12-07
forum: Desktop Environments
---

### Post by whs37 on 2010-12-07
As you probably can tell, I am brand new to Ubuntu. I managed to get started with it (in a Virtual Box running under Windows7). But I must have made a mistake because I lost my taskbar. I can minimize windows, but they disappear in the nowhere on the bottom of the screen.
Unfortunately I could not find a setting in Preferences where I can get the taskbar back. Your guidance would be appreciated.

---

### Post by yiannis66 on 2010-12-07
go to the top taskbar and right click and go to "new taskbar"
Klick on it and choose "bottom taskbar" .Now you have one.
With right klick on the bottom taskbar you can import anything you want.

---

### Post by karthick87 on 2010-12-07
Did you lost your gnome panels?If yes then execute the following one by one in terminal to get back your panel.
```
gconftool --recursive-unset  /apps/panel
```
```
rm -rf ~/.gconf/apps/panel
```[COLOR=#ff0000][B][I][FONT=Verdana]
[/FONT][/I][/B][/COLOR]```
pkill gnome-panel
```

---

### Post by matt_symes on 2010-12-07
Hi

It sounds like you have lost your window list applet on the panel.  

Right click on an empty space in the panel and select add to panel. Scroll down to 'window list' and select Add.

Kind regards

---

### Post by whs37 on 2010-12-07
Thanks guys for all th good answers. I will try that once I have my vBox fired up. That leads me to a new question: karthick suggested I use commands. As a bloddy beginner I have not yet figured out how to use the command line. In Windows I use Command Prompt a lot (in fact I teach classes about it - LOL), but for Ubuntu I need some guidance how to get to the equivalent of Command Prompt. Thanks.

---

### Post by whs37 on 2010-12-07
> **matt_symes said:**
> Hi
 
It sounds like you have lost your window list applet on the panel. 
 
Right click on an empty space in the panel and select add to panel. Scroll down to 'window list' and select Add.
 
Kind regards
 Now things are starting to come together. I got my taskbar back, I got the Applets. I am learning this Ubuntu. Now I have to figure out how to work with commands. Thanks again everybody.

---

### Post by karthick87 on 2010-12-07
Mark this thread as [COLOR=Red][SOLVED][/COLOR]

---

