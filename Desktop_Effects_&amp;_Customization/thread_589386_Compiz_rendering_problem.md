---
title: "Compiz rendering problem ?"
date: 2007-10-24
forum: Desktop Effects &amp; Customization
---

### Post by anarchypower on 2007-10-24
Dear community, 

I am running Ubuntu 7.10 with Compiz. Everything works fine, yet I am having some problems. I added a screenshot to show what my problem is:

[IMG]http://users.pandora.be/anarchypower/Screenshot.jpg[/IMG]

It happens when I move a window using the wobbly effect. My desktop cube has the same problem. I don't know why this is happening. Maybe it's because of my gpu driver? I have a NVIDIA 7900 GTX and I installed the restricted drivers...

I did not have this problem when running Ubuntu 7.04. Back then I used Envy to install my NVIDIA drivers. I did not use Envy under Ubuntu 7.10 because Envy does not allow me to read the temperature of my gpu.

Did anyone encounter the same problem as me? Let me know...

Any help is appreciated :)


Greetings

---

### Post by anarchypower on 2007-10-27
Bump :KS

---

### Post by anarchypower on 2007-11-05
Final Bump...

---

### Post by psyopper on 2007-11-05
The screenshot is nice but I'm not sure what you are looking at. Are you trying to show us that the window stops "wobbling" and looks like this when it comes to rest?

---

### Post by anarchypower on 2007-11-05
It looks like this when it is still wobbling...It doesn't wobble smooth...
Same goes for my cube. When I move the cube, it also displays horizontal misplacements...

---

### Post by FuturePilot on 2007-11-05
Press Alt+F2 and type 
```
nvidia-settings
```
Go through the settings and check anything that says Sync To VBlank
Then restart Compiz
If that works then you probably want those settings to load on login, so go System>Preferences>Sessions and add an item.
For the command add this
```
nvidia-settings --load-config-only
```
Also go into the Advanced Desktop Effects Settings and under the General Options go to the Display Settings tab and check Sync To VBlank.
Be careful with that option though because if you use suspend, it won't come out of suspend correctly due to a bug in the driver.

---

### Post by anarchypower on 2007-11-06
Wonderfull :guitar:

It works! I thank you very much :)

---

