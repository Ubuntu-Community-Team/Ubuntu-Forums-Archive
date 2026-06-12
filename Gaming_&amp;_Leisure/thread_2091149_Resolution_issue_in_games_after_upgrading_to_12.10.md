---
title: "Resolution issue in games after upgrading to 12.10"
date: 2012-12-04
forum: Gaming &amp; Leisure
---

### Post by amitst on 2012-12-04
After upgrading my OS to 12.10 I noticed that all games with fullscreen are messed up. I can see only part of the game screen in my monitor (the fullscreen mode doesn't resize the screen to fit my monitor, instead I can see partial screen on my monitor). Any tips? :confused:

---

### Post by amitst on 2012-12-04
I removed many .* directories from my home dir (but not the game config dir, e.g. .tremulous). This reset all my preferences and the screen started looking fine. However, after some time (2-3 hours), this issue has started appearing again suddenly (I entered exited game multiple times). Not sure what might cause this.

Here is my version detail,
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.10
Release:	12.10
Codename:	quantal

---

### Post by Espionage724 on 2012-12-05
I believe I can confirm this. My native resolution is 1600x900. A game I play with Wine has to be 1024x768 (well, doesn't "have" to, but I want it to lol). The screen resolution itself switches to 1024x768, and the game itself seems to be the right resolution too, but it's not centered, and gets cut off on the bottom and right side.

---

### Post by xREDEMPTIONx on 2012-12-06
What graphics cards and drivers are you guys using? It's possible the issue lies there.

---

### Post by amitst on 2012-12-07
No, it seems the issue lies with my home directory settings. I am using "Intel® 945G x86/MMX/SSE2" card and it is shown in System Settings -> Details -> Graphics.

Secondly, I am not running the game through wine. All GNU/Linux based games are giving this issue.

I created a temporary account and launched the game. It launched just fine. So I have a workaround to play games from this account. However, I was interested in knowing what kind of files in home directory decide the resolution etc.

I have also posted details on this issue at [http://ubuntuforums.org/showthread.php?t=2091538](http://ubuntuforums.org/showthread.php?t=2091538)

---

### Post by amitst on 2012-12-07
Strange. Now I am seeing the same issue with the temporary login. Yesterday it was working properly. I guess I don't have any workaround after all. Any tips?

---

### Post by amitst on 2012-12-08
The issue got resolved after installing Gnome Shell and using it while logging in.

I am wondering why I did take so much time to find it. It is definitely better (at least in terms of performance) than Unity Dash.

---

### Post by kabup2 on 2013-09-13
Me too, exactly the same issue. Before the upgrade (from Ubuntu 12.04 to 12.10) all was running fine, then I can't get the corret resolution.
My screen is 1650x1080, ingame it is 1024x768. All I can see from the game screen is the top left area, about 1/4.
If I switch to the 1024x768 before entering the game, is seems correct. But is a little annoying, it used to be automatic.

Changing to Gnome Shell doesn't work for me, I'm using it already. I left the unity a long time ago... :)

---

