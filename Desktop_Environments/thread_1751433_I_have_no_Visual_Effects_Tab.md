---
title: "I have no Visual Effects Tab"
date: 2011-05-06
forum: Desktop Environments
---

### Post by RyanMcD86 on 2011-05-06
Hi. i just wanted to see if someone could help with getting my visual effects tab to show up in the Appearance Preferences. for some reason it wont show up, and I'm not able to get compiz installed because i cant change the settings in there.

---

### Post by matt_symes on 2011-05-06
Hi

> **RyanMcD86 said:**
> Hi. i just wanted to see if someone could help with getting my visual effects tab to show up in the Appearance Preferences. for some reason it wont show up, and I'm not able to get compiz installed because i cant change the settings in there.

If you are running Unity 3D then Compiz should be running by default.

Just install compiz settings manager.

From a terminal

```
sudo apt-get install compizconfig-settings-manager
```

Enter your password. It will not be echoed to the screen.

Look for the Unity plugin under the desktop section.

Kind regards

---

### Post by RyanMcD86 on 2011-05-08
Hey. i did that. however i still don't see a visual effects tab. i had to change the window key value to metacity because im not getting the buttons at the top of windows to show up while im running compiz. anyone have any idea on what i can do to get compiz to work?

---

### Post by Copper Bezel on 2011-05-08
Changing the key to Metacity changes your default window manager to Metacity. When you're using Compiz, Metacity doesn't provide your window decorations anymore; Compiz uses a process called gtk-window-decorator to imitate Metacity's decorations. I understand that there are some differences in how this is handled in 11.04, including the fact that there is no Visual Effects tab (primarily because it would break Unity,) but what happens when you run ```
gtk-window-decorator --replace
``` ?

---

### Post by matt_symes on 2011-05-08
Hi

I was playing around with this the other day. If i remember correctly it needs to be

```
unity-window-decorator --replace
```

I will just double check though.

Kind reagrds

---

### Post by RyanMcD86 on 2011-05-08
no luck. the only thing that works is 
```
metacity --replace
```

---

### Post by Krytarik on 2011-05-08
Please see this troubleshooting guide, especially regarding the possibly missing packages and disabled "Window Decoration" plugin:
[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

Greetings.

---

### Post by RyanMcD86 on 2011-05-08
No luck with that one either. in fact i went to change it to desktop cube again, and all the settings got messed up. Now its even worse than before. []("http://ubuntuforums.org/member.php?u=1187548")

---

### Post by sikander3786 on 2011-05-09
> **RyanMcD86 said:**
> No luck with that one either. in fact i went to change it to desktop cube again, and all the settings got messed up. Now its even worse than before. []("http://ubuntuforums.org/member.php?u=1187548")
For enabling the cube, I would suggest to take a look here.

[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

---

