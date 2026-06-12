---
title: "PLEASE I need some help"
date: 2010-01-15
forum: Desktop Environments
---

### Post by Ba7r on 2010-01-15
[FONT=Tahoma][SIZE=3][COLOR=Blue]**Hi, **

firstly I was a fan of microsoft " _**windows**_ ", I'm a new user for Linux, I liked It so much, I'm doing my best to know everything about UBUNTU, I find It good to search and find solutions otherwise windows, I've learned some commands, I'm trying to know more, But I'm now facing some problem that I can't install ( _**wine and beryl**_ ) on my system **_Ubuntu 9.10_** and every time I write the command to setup It in terminal It shows that ( the package of this programs doesn't exist ), 
note: I've a good viga card and my PC is some kinda Good, but I don't know where's the problem, [PLEASE]("http://google-yahoo-user.blogspot.com") I need some help guys 

**Reagrds **
**Muhammed**
[/COLOR][/SIZE][/FONT]

---

### Post by d3v1150m471c on 2010-01-15
you don't need beryl. You have compiz which is essentially the exact same thing. Install compiz-settings-manager in synaptic. afterwards:

system > preferences > compiz settings manager...

this will allow you to make all the adjustments you need to compiz. stuff like your 3d desktop cube and all that cool jazz. If you want a really visually appealing theme manager check out emerald.

---

### Post by Enigmapond on 2010-01-15
beryl is out of date and I would suggest compiz for the desktop effects. Both wine and compiz are listed in the default repositories. try going through Synaptic.

---

### Post by mk1w86 on 2010-01-15
> Install compiz-settings-manager in synaptic.

The exact package name is compizconfig-settings-manager ;) so to install run:

```
sudo aptitude install compizconfig-settings-manager
```

I'm not sure what problems you're having with wine but to install it run:

```
sudo aptitude install wine
```

---

### Post by 3Miro on 2010-01-15
Applications -> Ubuntu Software Center, then search for wine and install. Wine beta is probably better, it may be less stable but it will do more things than wine 1.0. For how to run individual games, try winehq.org and their database.

From System -> Administration -> Synaptic Package Manager, install compiz config manager (search for it). After it installs, go to System -> Preferences -> Compiz Config Manager and you can edit hundreds of effects and shortcuts. Compiz is the default effects engine for Ubuntu and before you get comfortable with the system you probably should play it safe. Besides, I am not sure Beryl has any effects that compiz is missing.

When you want to install software in Ubuntu, always first check with Ubuntu Software Center and then Synaptic Package Manager. You should try other methods only if the app that you want is not listed there.

---

### Post by Ba7r on 2010-01-15
[FONT=Tahoma][SIZE=3][COLOR=Blue]_**[FONT=Arial Black][COLOR=Red]thanks ALL for helping me[/COLOR][/FONT] :) **_, It's okay now I installed wine and compiz-settings-manager successfully, but I tried to make It 3D but It doesn't work, so I'll be more noisy and I'll ask why It didn't work the [3D]("http://google-yahoo-user.blogspot.com") effects ..
[/COLOR][/SIZE][/FONT]

---

### Post by mk1w86 on 2010-01-15
> **Ba7r said:**
> [FONT=Tahoma][SIZE=3][COLOR=Blue]_**[FONT=Arial Black][COLOR=Red]thanks ALL for helping me[/COLOR][/FONT] :) **_, It's okay now I installed wine and compiz-settings-manager successfully, but I tried to make It 3D but It doesn't work, so I'll be more noisy and I'll ask why It didn't work the 3D effects ..
[/COLOR][/SIZE][/FONT]

Do you mean compiz it not working?

If it is not make sure any propriety graphics drivers are installed.  To check this go to:

System >> Administration >> Hardware Drivers

---

### Post by Ba7r on 2010-01-16
[FONT=Tahoma][SIZE=3][COLOR=Blue]I tried everything and I installed all what you have told me but still the same :)

regards
Muhammed
[/COLOR][/SIZE][/FONT]

---

### Post by Ba7r on 2010-01-16
[FONT=Tahoma][SIZE=4][COLOR=Blue]I checked[/COLOR] [FONT=Arial Black][SIZE=3]_**Hardware Drivers**_[/SIZE][/FONT] [COLOR=Blue]and I found that I'm installing the highest version of[/COLOR] [FONT=Arial Black][SIZE=3]NVIDIA[/SIZE][/FONT] >>> ( [FONT=Arial Black]_**[SIZE=3]NVIDIA accelerated graphics drivers (version 185) [Recommended][/SIZE]**_[/FONT] )

[COLOR=Blue]this is my [Viga Card info]("http://google-yahoo-user.blogspot.com")
[/COLOR]
[COLOR=Red][FONT=Arial Black][SIZE=3]*Graphic Card Information[/SIZE][/FONT]
Graphic Processor: GeForce 6150SE nForce 430
VBIOS Version:      05.61.32.22.01
Memory:                512 MB
Bus Type:              Integrated
Bus ID:                 0:13:0
IRQ:                     22
X Screens:            Screen 0
Display Devices:   DELL M783S (CRT-0)[/COLOR]

[COLOR=Blue]* But still I can't make It 3D ,, I know that I annoyed you ,, but anyway thanks for helping me

[FONT=Verdana][SIZE=3][B]Regards
Muhammed[/B][/SIZE][/FONT][/COLOR] 



[/SIZE][/FONT]

---

### Post by huviduc on 2010-01-18
Is any part of Compiz working? When you say that you cant get 3D to work, what exactly are you trying and what result are you getting? The more information you can provide, the better chances you will have of getting it resolved. 

Also, please see this link ([http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)) it should be able to help you get most of the effects you could want.

---

### Post by nilarimogard on 2010-01-18
Ba7r, 

After enabling the restricted Nvidia drivers (which I see you have already), right click on your desktop and select "Change desktop background", then on the last tab called "Visual Effects", check the "Extra" option. If it works (you don't get any error), Compiz will work. 

To get the 3D cube, go to *System > Preferences > CompizConfig Settings Manager* and there go to "General Options", then on the last tab called "Desktop Size" enter 4 for "Horizontal Desktop size". Finally, make sure the following Compiz plugins are enabled (still under *System > Preferences > CompizConfig Settings Manager)*: "Desktop Cube" and "Rotate Cube".

Now, to see the cube, hold the Ctrl + Alt keys and drag with your left mouse button. 

Good luck with Ubuntu! :)

---

### Post by Ba7r on 2010-01-21
> **nilarimogard said:**
> 

Now, to see the cube, hold the Ctrl + Alt keys and drag with your left mouse button. 

Good luck with Ubuntu! :)

[FONT=Tahoma][SIZE=3][COLOR=Blue]Hi, 
1st I want To thanks all friends who tried to help me, and also I want to apologise about the annoy I did to turn the 3D on, Finally I want to thanks this man " [COLOR=Red]_**[FONT=Arial Black]nilarimogard[/FONT]**_[/COLOR] " :) ,, loool simply It was working but I didn't know how to use It ( Excuse me It's my 1st time using Linux ), But now I'm happy I did get ride of WINDOWS lol

My best regards for all

[FONT=Arial Black][COLOR=Blue]**Muhammed**[/COLOR][/FONT][/COLOR][/SIZE][/FONT]

---

