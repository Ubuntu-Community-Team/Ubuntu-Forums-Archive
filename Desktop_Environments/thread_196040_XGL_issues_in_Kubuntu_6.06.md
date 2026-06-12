---
title: "XGL issues in Kubuntu 6.06"
date: 2006-06-13
forum: Desktop Environments
---

### Post by nnp on 2006-06-13
Hey, I know this has been done to death in many places at this stage but after 3 hours of playing around with stuff i think its about time I asked someone. I'm using kubuntu 6.06. I followed the tutorial at 

[http://ubuntuforums.org/showthread.php?p=845077](http://ubuntuforums.org/showthread.php?p=845077)

exactly. 

My problem though is this. When I restart kdm it immediately jumps to that black screen with kubuntu at the top (the one that appears on startup and shutdown saying whats loading/closing etc) except there is no text (besides the kubuntu logo). After about 30 seconds it just drops back to the virtual terminal. My drivers etc are fine (using an nvidia 6600GT)and i've tried with the following file in .kde/Autostart/

> 
#!/bin/bash
#compiz --replace gconf decoration dock wobbly fade minimize cube rotate zoom scale move resize place state switcher trailfocus water bs widget & gnome-window-decorator

compiz --replace gconf & gnome-window-decorator


with both the currently commented out line and the one thats in use. Its the same either way. I tried also using the default kdmrc, just to see what would happen, and kde loaded fine and gconf was in the settings menu but the keyboard didnt work and once a window was opened it couldnt be closed or moved.

If any other details are needed I'll provide them.

Thanks,
NNP

---

### Post by johneedoe on 2006-07-29
I had the same problem, and tried again using this guide and now it works
Good Luck

[http://www.compiz.net/viewtopic.php?id=1067](http://www.compiz.net/viewtopic.php?id=1067)

---

### Post by stiankarlsen on 2006-07-29
Or you could try this insanely easy method...

[http://justpretending.net/wp/2006/06/12/ubuntu-users-enable-xgl-on-dapper-drake/]("http://justpretending.net/wp/2006/06/12/ubuntu-users-enable-xgl-on-dapper-drake/")

---

