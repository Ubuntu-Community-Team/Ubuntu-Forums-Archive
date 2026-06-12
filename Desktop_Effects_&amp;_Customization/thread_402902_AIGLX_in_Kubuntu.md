---
title: "AIGLX in Kubuntu?"
date: 2007-04-06
forum: Desktop Effects &amp; Customization
---

### Post by Lateralus@desktop on 2007-04-06
Am I missing something? I followed the steps to get AIGLX working in Ubuntu (And it worked, every time, without fail in my Ubuntu install), but I follow the same steps in Kubuntu, and it doesnt work. 

I followed the instructions from here: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

I've got an ATI Radeon 9800 Pro, and I'm running Kubuntu Edgy.

$ glxinfo | grep vendor returns this: 
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)

which according to the radeon driver wiki is correct and should work. Yet when I try
$ glxinfo | grep "direct rendering" it returns this:
direct rendering: No
In Ubuntu it returned a yes and I could use Beryl at a rather steady 130fps, but I followed the _exact_ steps I took before, and Kubuntu returns a no:( 

If anyone could help me out here, their assistance would be greatly apreciated. 

Also, I think this info could go into a seperate Kubuntu wiki or something. To help people who are suffering a similar problem.

---

### Post by lazyrussian on 2007-04-06
I actually installed beryl last night using these two walkthoughs - 

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#C](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#C)

[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL)

Try it and see what happends

(I have an ati radeon xpress and I am runninf Kubuntu) -

---

### Post by Lateralus@desktop on 2007-04-06
Thanks for the guides. Not that I want to sound picky, but both those guides are for XGL + Beryl... I was looking for AIGLX and Beryl. I've not once been able to get XGL actually working, and it always seems to have disagreements with my Xorg.

---

### Post by lazyrussian on 2007-04-06
Oh, I'm sorry. I misread AIGLX for XGL...twice lol.

Try this: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX)

Sorry I can't be of any more help.

---

### Post by Lateralus@desktop on 2007-04-06
Thanks for that link, lazyrussian. 

$ glxinfo | grep "direct rendering" now shows a very pleasing 'Yes' :) 

The only problem is, is when I type 'beryl-manager' into Konsole, my entire pc locks up. And I mean _totally_ locks up, Cntrl+Alt+Backspace does nothing, tapping the NumLock key doesnt do anything. The only solution is a full system restart...

I'm thinking this is something to do with KDM loading before beryl on startup. I cant set beryl to load on startup, 'cos I'm not 100% sure that will solve anything.

---

### Post by lazyrussian on 2007-04-06
I'm glad you see the 'yes' :)

As for the reboot, That's a very strange problem. Beryl Forums will probably have the answer.

---

### Post by Lateralus@desktop on 2007-04-06
Tiny update on the restart issue. After adding a few things to my Xorg.conf, when I start beryl-manager, it crashed my pc and sends me back to my login screen...

I'll go check out the Beryl forums, thank you.

---

### Post by lazyrussian on 2007-04-06
No problem, best of luck!

---

