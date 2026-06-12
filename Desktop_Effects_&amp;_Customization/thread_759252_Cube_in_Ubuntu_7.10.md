---
title: "Cube in Ubuntu 7.10"
date: 2008-04-18
forum: Desktop Effects &amp; Customization
---

### Post by enazguy on 2008-04-18
I've seen videos on youtube where a person used ubuntu and goes to into a cube type window where he can pick and choose what to look at. I've been trying to find out how do this for a while. Is it even possible or is it just eye candy for people to look at?

---

### Post by overdrank on 2008-04-18
> **enazguy said:**
> I've seen videos on youtube where a person used ubuntu and goes to into a cube type window where he can pick and choose what to look at. I've been trying to find out how do this for a while. Is it even possible or is it just eye candy for people to look at?

HI and what is the model of the graphics card? Have you tried to enable the effects under system, preference, appearance. Then select the visual effects tab.

---

### Post by xradarx on 2008-04-19
you need Compiz Fusion

---

### Post by ad_267 on 2008-04-19
Compiz fusion is installed by default in 7.10. If you go to System -> Preferences -> Appearance and then go to the Visual Effects tab can you select normal or extra effects? If so then you are using compiz-fusion.

In order to enable the cube you need to download the compizconfig-settings-manager package:
```
sudo apt-get install compizconfig-settings-manager
```

Once that is done then you can go to System -> Preferences -> Appearance -> Visual Effects and click on Custom. From there you need to go to General Options -> Desktop Size and change Horizontal Virtual size to 4, and leave the other options at 1. Then you can go back and enable the Desktop Cube and Rotate Cube effects and any other options you want. You may need to restart X to get the effects to work by logging out and logging back in or pressing ctrl-alt-backspace

---

### Post by enazguy on 2008-04-19
I have compiz fusion enabled but I can't seem to get the cube. Is there a certain button combination?

---

### Post by overdrank on 2008-04-19
> **enazguy said:**
> I have compiz fusion enabled but I can't seem to get the cube. Is there a certain button combination?

HI and that would be ctrl, alt, single click and hold on the mouse. Then move the mouse to rotate cube.

---

### Post by prshah on 2008-04-19
> **enazguy said:**
> I have compiz fusion enabled but I can't seem to get the cube. Is there a certain button combination?

Usually Ctrl+Alt+MouseButton1 or MouseButton3.

Also you have to make sure that you have 4 desktops, and that the rotate cube plugin is active. To check this, open System->Preferences->Advanced Desktop Effects Settings and make the following changes: (See attached screenshot)

In "General Options"-"Desktop Size" set Horizontal Virtual Size to "4" and the rest to "1", then go back to the main screen.

In the main screen, "Desktop" section, enable the "Desktop Cube" and "Rotate Cube".

---

