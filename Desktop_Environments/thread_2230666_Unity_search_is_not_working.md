---
title: "Unity search is not working"
date: 2014-06-20
forum: Desktop Environments
---

### Post by hermanbergwerf on 2014-06-20
I'm really getting sick of the Unity dash search. It takes multiple seconds to show the dash, I have to check the application filter over and over again and if it cannot find applications sometimes (I only use it to find applications) When it can find applications, it takes at least 10 seconds to find firefox when I type 'firefox'. The Unity dash is even capable of freezing my whole desktop environment for seconds and it swallows CPU like I'm rendering a heavy Blender 3D scene. This forces me to run applications via the terminal (I'm not against terminal usage but sometimes buttons are just more relaxing) Is there any alternative besides switching to KDE or another environment? The slowness has sustained through several Ubuntu distribution updates so far.

---

### Post by vanadium on 2014-06-20
I recognize your issue of the application filter switching off. I do, however, not have the severe performance issues you have. On cold start, it takes several seconds for the dash to find an item, but after that, the speed is good. Perhaps your system has relatively lower specifications? If indeed it is an older system, I think there is no other option than switch to a desktop environment with lower system requiremements, or else use another launch utility instead of the Dash (leaving not much reason to continue using Unity anyway). Kupfer or Launchy are two utilities that allow you to quickly launch applications by typing a few letters of the name.

---

### Post by grahammechanical on 2014-06-20
My system has an Intel core 2 Duo CPU and I GB RAM and I do not see any slowness in the Dash. In fact the Dash will often find an application before I finish typing its name. It even finds apps dispite my mis-typing of the name.  and it is doing this while I have 3 Libreoffice windows open and listening to a BBC radio program and recording it. I think that the search feaure is designed to respond to the users search habits.

If we are using 14.04 we can turn off online search. I have not done that but it might speed the Dash searches a little bit.

Regards.

---

### Post by buzzingrobot on 2014-06-20
I've seen suggestions that Unity's default real-time creation of a blurred background for the Dash can especially task weak video cards.  If Unity-Tweak-Tool is installed, it provides an option to use a static background.

---

### Post by vanadium on 2014-06-20
That might indeed probably solve your "freeze" issue. Install Unity Tweak Tool from Software center. On the "Search" tab, turn "Background blur" off.

---

### Post by hermanbergwerf on 2014-06-20
I tried most of that stuff. I don't believe my system is too slow for application search. When I clear the software center cache, reset unity and login again, everything is fine for one day or something:
```
rm ~/.cache/software-center -R
unity --reset &
```
I guess there is something somewhere getting slow over time.

---

### Post by hermanbergwerf on 2014-06-21
Same problem when I restarted my computer this morning. But after running:
```
[COLOR=#000000]rm ~/.cache/software-center -R[/COLOR]
[COLOR=#000000]unity --reset &
```
and logging out and in. Everything was just working. Is my unity broken or something.

[/COLOR]

---

