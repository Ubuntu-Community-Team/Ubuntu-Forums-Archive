---
title: "new to beryl"
date: 2007-05-27
forum: Desktop Effects &amp; Customization
---

### Post by windows hater on 2007-05-27
im running a ATI RADEON X 1550 GRAPHICS  and i want to runn baeryl but ever time i run it my screen flickers and nothing happens and i just installed ubuntu fiesty and dont noe much to start can some one give a step by step

---

### Post by Ub1476 on 2007-05-27
The reason your screen flashes is that you aren't running in a XGL session.
[B]
step-by-step[/B]

Uninstall beryl:
```
sudo aptitude remove xserver-xgl beryl beryl-core beryl-manager beryl-plugins beryl-plugin-data beryl-settings beryl-setting-bindings libberyldecoration0 libberylsettings0 libemeraldengine0
```

Follow this guide to install Beryl&XGL:

[Guide]("http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_install_Beryl_.28ATI.29")

Scroll down to ...Alternate method: Using closed source FGLRX drivers from ATI... and follow the guide from there.

Hope that helps.

---

### Post by windows hater on 2007-05-27
it didnt work it wont even install beryl i think i made it worse now

---

### Post by Znupi on 2007-05-27
I used this guide, short and simple: [https://help.ubuntu.com/community/Beryl/ATI/Feisty](https://help.ubuntu.com/community/Beryl/ATI/Feisty)
Although I don't know if it's going to work considering you have 2 failed beryl installations on your PC.

[SIZE=1]Offtopic: your nickname is too generic. 75% of the people on this forum could use the same nickname, :lol:[/SIZE]

---

### Post by windows hater on 2007-05-27
im must be really really stupid ok that did not work and is there like a code to erase this bc i really want beryl and it just not working right now it wont install so is there a command to erase everthing i just did and start fresh i feel like i make it worse as i go on

---

### Post by Znupi on 2007-05-27
You probably just installed Ubuntu, too, right? If I were you, I'd reinstall Ubuntu and try my link again, it only takes like 30 minutes. Of course, if there's an easier way, without reinstallation, someone will probably post it. I don't know any such way.

---

### Post by windows hater on 2007-05-27
so reinstall it and do u think it well work then for sure or is it ur best guess

---

### Post by Znupi on 2007-05-27
It worked for me the first time around, with that tutorial. I can't be sure about you, but chances are it will work for you, too.

---

### Post by Ateo on 2007-05-27
> **windows hater said:**
> so reinstall it and do u think it well work then for sure or is it ur best guess

It'll work if you follow the directions correctly. That's the point. So, if you feel you messed up, start over with a nice fresh install of Ubuntu.

---

### Post by windows hater on 2007-05-27
i done it ever thing it said with a fresh install how can i test to see if it works is there a shortcut or something i need for it to work ??

---

### Post by Cresho on 2007-05-27
dont know what you mean but if you dont have beryl setup at astart up, then you need to activate it mannyally by going into system and beryl manager. after beryl starts up, then you hold both left and right click mouse while cursor is on screen and just move it.
 
there are tons of settings in the beryl manager.

---

### Post by Znupi on 2007-05-27
Make sure you are logged into your Xgl session.

---

### Post by windows hater on 2007-05-27
i did that it is on xgl and i followed the guide to but beryl still dosnt want to run

---

### Post by windows hater on 2007-05-27
Checking for XComposite extension               : failed
 happens all the time i install beryl  solution

---

