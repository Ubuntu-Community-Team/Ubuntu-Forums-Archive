---
title: "Team Fortress 2 crash"
date: 2007-11-01
forum: Gaming &amp; Leisure
---

### Post by Tylerofl on 2007-11-01
Steam appears to be working fine (although a little slow), and Half-life 2 episode 1 works GREAT (i've yet to try CS : S). TF2 appears to work fine in the menus, but as soon as the loading screen is done and you choose a side, it shows a frozen image of a place in the level and it completely freezes. I have to force quit to get out.

Is anyone else having this problem? Word on the street is that TF2 works great in Wine. (by the way, I'm using 0.9.48)

---

### Post by SM0k3 on 2007-11-02
> **Tylerofl said:**
> Steam appears to be working fine (although a little slow), and Half-life 2 episode 1 works GREAT (i've yet to try CS : S). TF2 appears to work fine in the menus, but as soon as the loading screen is done and you choose a side, it shows a frozen image of a place in the level and it completely freezes. I have to force quit to get out.

Is anyone else having this problem? Word on the street is that TF2 works great in Wine. (by the way, I'm using 0.9.48)

are you using Wine 0.9.48? I had that exact freezing problem until I downgraded to 0.9.46, maybe you should try that.

Good luck

---

### Post by escobar_ on 2007-11-02
What he said.

I have 0.9.46 too and TF2 runs perfectly.

---

### Post by Tylerofl on 2007-11-02
Uh huh, I was on 0.9.48 (number got turned into an emoticon). I went back to 0.9.46 and was able to play a game. I exited the program, and went back later, and now I can't get past the load screen when you join/create a game. Are there any settings I need to change in winecfg?

---

### Post by Polygon on 2007-11-03
how did you guys even get to the menu? when i start the game, it plays the valve intro video, and then as soon as it tries to load the menu, it just crashes to desktop, no error or anything

i read some guide on how to get it running, by adding a bunch of registry key values...and it still crashes. any suggestions?

---

### Post by pfred on 2007-11-04
> **SM0k3 said:**
> are you using Wine 0.9.48? I had that exact freezing problem until I downgraded to 0.9.46, maybe you should try that.

Good luck
I am having the same problem with freezing and getting the looping sound crash just after selecting a team. I am using Wine 0.9.48 since that was the one in synaptics. 

So my question now is: What would be the best way to downgrade o 0.9.46? I have Steam, TF2, CS:S and COD2 installed already. Would I have to uninstall them before downgrading Wine?

---

### Post by SM0k3 on 2007-11-04
> **Tylerofl said:**
> Uh huh, I was on 0.9.48 (number got turned into an emoticon). I went back to 0.9.46 and was able to play a game. I exited the program, and went back later, and now I can't get past the load screen when you join/create a game. Are there any settings I need to change in winecfg?

Not sure what the problem is but the only thing I messed with in the winecfg was checking "emulate a virtual desktop" and giving it a resolution of 1024x768 under the "graphics" tab. You can also try going to your Audio tab and change "hardware Acceleration" to "Emulation" and check "Driver Emulation" right below it.

EDIT: I almost forgot in your "graphics" tab Change "Vertex Shader Support" to hardware and check "allow pixel shader" :D

If that doesn't work you'll probably have to wait until someone that has more experience chimes in on the issue since I'm fairly new to wine myself.

> **pfred said:**
> I am having the same problem with freezing and getting the looping sound crash just after selecting a team. I am using Wine 0.9.48 since that was the one in synaptics. 

So my question now is: What would be the best way to downgrade o 0.9.46? I have Steam, TF2, CS:S and COD2 installed already. Would I have to uninstall them before downgrading Wine?

When I downgraded most of my games still worked without reinstalling, but some of the games in steam disappeared somehow and I had to reinstall so all I can say is have your install CD's ready hah...you can uninstall wine using Synaptic package manager under system -> administration

You can get  the 0.9.46 version here ->  [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)


Good Luck & hopefully they will iron out some of these issues in the next release.

---

### Post by brainspank on 2007-11-04
> **pfred said:**
> So my question now is: What would be the best way to downgrade o 0.9.46? I have Steam, TF2, CS:S and COD2 installed already. Would I have to uninstall them before downgrading Wine?

I've switched back and forth with no problems.  9.46 didn't have the Tahoma font, so I avoid the problem by just copying them into c:\windows\fonts beforehand.

```

*(find tahoma fonts if you already have them - or go get them somewhere else)*
$ locate -r "tahoma.*\.ttf"
*(identify location of tahoma.ttf and tahomabd.ttf from 9.48 or windows partition)*
$ cp <files> ~/.wine/drive_c/windows/fonts/
$ sudo apt-get install wine=0.9.46-0ubuntu1

```

---

