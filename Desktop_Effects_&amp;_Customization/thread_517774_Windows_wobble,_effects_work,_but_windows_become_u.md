---
title: "Windows wobble, effects work, but windows become unresopnsive"
date: 2007-08-05
forum: Desktop Effects &amp; Customization
---

### Post by rainwalker on 2007-08-05
I just finished installing Compiz Fusion on my Inspiron 8600, running Feisty, upgraded from Edgy.
I have Beryl installed from when I used it on Edgy, and didn't uninstall it before I installed Fusion (because it's always worked).
Anyway, I thought I had successfully installed Fusion because it seemed to be running great, so I put the command I use to start it in my Startup Programs. The code I use is > compiz --replace -c emerald &
Before I get into the problems I'm having now, I have a question about that command; I run that from a terminal and it tells me all the stuff it's loading, and once it's finished and Fusion is running, I close the terminal. When I do that, my titlebars/window borders disappear for a second, then reappear using some theme I've never used before (rather than the Feisty New Human emerald theme it used before I closed the terminal). All of the effects work, though, and it all works normally.
So, thinking I'd gotten it figured out and working and that if it started up when I log in I would have that problem, because I wouldn't be closing any terminal that way, I put "Compiz Fusion" in my startup programs with that command to start it. I restarted and logged, and waited to see what would happen. My desktop seemed to load normally and Fusion started up (I know because of the shadows and stuff. 
So here I am, FINALLY getting some really nice, fast desktop effects working, and I'm ecstatic. Yay! Woohoo! And all that.
But when I clicked on one of the menus, "System" in this case, and went to "Preferences", the sub-menu would just appear. No wobbly fade-in, and nothing would be highlighted on mouseover. I could click stuff, though, and the windows would fade in like normal, but the applications themselves would be unresponsive. The only way I could get the GUIs to appear was by minimizing and then maximizing the window, and all that would do what update whatever was in it. In a text editor, for example, I could type whatever and it wouldn't show up. Minimize and maximize the window, and the text would be there, but I'd have to repeat that process to update the display every time. NOT FUN.
I stopped Fusion by starting Beryl Manager (that kills it somehow) and started it again from a terminal so I could see what it says. I started it with the same command (that's the only way I know how to start it), and again it messed up. I read through what was displayed in the terminal, and the only abnormal things I found are as follows:
> riley@Riley-laptop:~$ compiz --replace -c emerald &
[1] 25026

## Many "Initializing whatever"s here##

Initializing wobbly options...done
Gconf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/friction. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/spring_k. Settings from this path own't be read. Try to remove that value so that operation can continue properly.

## More initializations##

Initializing fade options...done
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

## Initializations again##

Initializing screensaver options...done
/usr/bin/compiz.real (splash) - Warn: Could not load splash background image "/data/splash_background.png" !
/usr/bin/compiz.real (splash) - Warn: Could not load splash logo image "/data/splash_logo.png" !


I haven't tried deleting those things it talks about because I don't know what they are.
I don't know what any of this means, except that I DO know that I have no "/data" directory.

I'm using an ATI RV350 Mobility Radeon 9600 M10, with the open-source drivers; The desktop effects never worked with the proprietary ones, but I've read something about using XGL...?

Anyway, does anyone have some ideas as to how I could fix this?

---

### Post by rainwalker on 2007-08-05
Alright, I tried again but left the terminal open instead of closing it.
I still had a few instances where menu items won't highlight, but at least it was using the right theme. 
I just closed the terminal and this is what happened:
1. Window borders/titlebars disappeared for about 5 seconds
2. Now that they have reappeared, they're using that theme I was talking about. I'll try to take a screenshot (it's going to be hard, read this third thing)
3. Windows are once again unresponsive, I'm typing this without actually seeing it

I guess I need a way to run the command, but keep it reunning. I'd run it from a terminal and keep the terminal open, but that seems stupid when I should be able to just fix the problem.

---

### Post by walkerk on 2007-08-06
> **rainwalker said:**
> Alright, I tried again but left the terminal open instead of closing it.
I still had a few instances where menu items won't highlight, but at least it was using the right theme. 
I just closed the terminal and this is what happened:
1. Window borders/titlebars disappeared for about 5 seconds
2. Now that they have reappeared, they're using that theme I was talking about. I'll try to take a screenshot (it's going to be hard, read this third thing)
3. Windows are once again unresponsive, I'm typing this without actually seeing it

I guess I need a way to run the command, but keep it reunning. I'd run it from a terminal and keep the terminal open, but that seems stupid when I should be able to just fix the problem.

press alt+f2 and run the command
```
compiz --replace -c emerald &
```

let me know..

---

### Post by walkerk on 2007-08-06
> **rainwalker said:**
> I just finished installing Compiz Fusion on my Inspiron 8600, running Feisty, upgraded from Edgy.
I have Beryl installed from when I used it on Edgy, and didn't uninstall it before I installed Fusion (because it's always worked).
Anyway, I thought I had successfully installed Fusion because it seemed to be running great, so I put the command I use to start it in my Startup Programs. The code I use is 
Before I get into the problems I'm having now, I have a question about that command; I run that from a terminal and it tells me all the stuff it's loading, and once it's finished and Fusion is running, I close the terminal. When I do that, my titlebars/window borders disappear for a second, then reappear using some theme I've never used before (rather than the Feisty New Human emerald theme it used before I closed the terminal). All of the effects work, though, and it all works normally.
So, thinking I'd gotten it figured out and working and that if it started up when I log in I would have that problem, because I wouldn't be closing any terminal that way, I put "Compiz Fusion" in my startup programs with that command to start it. I restarted and logged, and waited to see what would happen. My desktop seemed to load normally and Fusion started up (I know because of the shadows and stuff. 
So here I am, FINALLY getting some really nice, fast desktop effects working, and I'm ecstatic. Yay! Woohoo! And all that.
But when I clicked on one of the menus, "System" in this case, and went to "Preferences", the sub-menu would just appear. No wobbly fade-in, and nothing would be highlighted on mouseover. I could click stuff, though, and the windows would fade in like normal, but the applications themselves would be unresponsive. The only way I could get the GUIs to appear was by minimizing and then maximizing the window, and all that would do what update whatever was in it. In a text editor, for example, I could type whatever and it wouldn't show up. Minimize and maximize the window, and the text would be there, but I'd have to repeat that process to update the display every time. NOT FUN.
I stopped Fusion by starting Beryl Manager (that kills it somehow) and started it again from a terminal so I could see what it says. I started it with the same command (that's the only way I know how to start it), and again it messed up. I read through what was displayed in the terminal, and the only abnormal things I found are as follows:


I haven't tried deleting those things it talks about because I don't know what they are.
I don't know what any of this means, except that I DO know that I have no "/data" directory.

I'm using an ATI RV350 Mobility Radeon 9600 M10, with the open-source drivers; The desktop effects never worked with the proprietary ones, but I've read something about using XGL...?

Anyway, does anyone have some ideas as to how I could fix this?

Yes.. you are going to need to use XGL with your ATI card to get Compiz Fusion working. Take a look at this thread: [http://ubuntuforums.org/showthread.php?t=488385&highlight=Compiz+Fusion+ATI](http://ubuntuforums.org/showthread.php?t=488385&highlight=Compiz+Fusion+ATI)

---

### Post by rainwalker on 2007-08-06
Well it's actually running fine again, I don't know what the problem was/is...

---

