---
title: "Nvidia and ATI: Unity compatibility issue"
date: 2013-04-30
forum: Desktop Environments
---

### Post by spyderos on 2013-04-30
I recently installed Ubuntu 13.04, and came across this problem.
When I log in, my Unity bars do not appear.  I have the wallpaper and cursor, but not much else.  I have a Geforce 550 Ti Nvidia card, and despite changing drivers, I cannot get my unity bars to work.  I also have a internal ATI Radeon HD 3300 card, and my long term goal is to get Ubuntu working where I am driving my display with the internal Radeon, but I am still able to use the CUDA cores on the Nvidia card for Cycles rendering in Blender(the open-source 3d design suite)


When I run unity --replace, it gives me errors dealing with opengl and glx(varying with the current driver)


The recurring error is: compiz (core) - Error: Plugin 'opengl' not loaded.


The cards are once again:
Nvidia GeForce GTX 550 Ti - external
ATI Radeon HD 3300 - internal

Your help is greatly appreciated.

p.s. I know that having both cards working together works in Windows 8, so I sincerely hope it is possible in Linux, because I hate using Windows.

---

### Post by spyderos on 2013-04-30
So by creating a new account, I was able to get back my unity bars, however I am still trying to get to my CUDA cores.

---

### Post by bogan on 2013-05-01
H!, **spyderos,**

There are several things that can cause effects similar to your report;  for instance many report it after installing a video driver, and a  Plugin-not activated.

I had three 13.04 installations all showing the same blank Desktop, but Unity running OK in fallback or in another account.

Check out my Thread in the  Ubuntu +1 forum, there are several examples  there, including how to check and reset Plugins, and of ways different people attacked the problem, and cured it - or  not. Take your pick.

[http://ubuntuforums.org/showthread.php?t=2136435](http://ubuntuforums.org/showthread.php?t=2136435)

The essential thing is to note and Post what error messages you get, if any, from which command.

Chao!, **bogan.**

---

### Post by Grafens on 2013-05-01
Generally speaking if your having openGL issues you should turn off effects/compiz.

Under blender > user preferences > system > compute device can you see your nvidia card in the drop down box. If its not listed do some research on the nouveau bumblebee drivers as they allow you to choose which graphics card to use for specific apps.

---

### Post by bogan on 2013-05-01
Hi!,** Grafens**,

Please clarify what you Posted.

 How and where can those instructions be accessed ?  Or are they particular to Kubuntu??>  Generally speaking if your having openGL issues you should turn off effects/compiz.

Under blender > user preferences > system > compute device can  you see your nvidia card in the drop down box. If its not listed do some  research on the nouveau bumblebee drivers as they allow you to choose  which graphics card to use for specific apps. Is: "turn off effects/compiz" equivalent to logging in to Gnome shell, Classic or fallback (no effects) ??

When I entered 'blender'  in a terminal, there was no man page, and It said it was not installed, but I could do so with apt-get,

Luckily I didn't do so, as Google tells me:>  **Blender is not the kind of software you can launch into and grope  about until you find your way. It's not like exploring an unfamiliar  city. It's more like flying a jet airplane. If you hop into the pilot's  seat without knowing the fundamentals, you'll be lucky to ever get off  the ground, and it'd take a miracle for you to reach your destination  safely.**Seems a bit much just to list my Graphics card!!

Thanks for the response, none the less.

Chao!,** bogan.**

---

### Post by Grafens on 2013-05-02
> [COLOR=#000000]How and where can those instructions be accessed ? Or are they particular to Kubuntu??[/COLOR]
For kubuntu/KDE you can turn off effects in the system settings.
For unity things seem a bit more complicated. A quick google turned this up.
[http://askubuntu.com/questions/138622/how-to-disable-all-unity-animations](http://askubuntu.com/questions/138622/how-to-disable-all-unity-animations)
> Under blender > user preferences > system > compute device can you see your nvidia card in the drop down box.

As for this bit I was refering to the settings within blender itself.
> Luckily I didn't do so, as Google tells me:
You could compare it to a planes cockpit with all those hundreds buttons. It's not that bad once you get familiar with it, takes a lot of patience though. Anyway if your interested there's loads of tutorials on youtube just start with the basics first.
Grafens

---

### Post by spyderos on 2013-05-02
First of all, I want to thank both of you for your responses.  I'm sorry I didn't respond earlier, but I had a huge 32 hour render in windows. :(

Now, my trouble seems to start once I install nvidia drivers.  The problem is that without them, blender doesn't have access to the nvidia gpu. (including in the blender > preferences > system > compute device)
I currently am not having opengl problems, but I am running on the nouveau drivers.  So rather than do something stupid like just spur of the moment install the nvidia drivers, I am going to give this info to you guys, and let you help me.

Thanks again.

---

