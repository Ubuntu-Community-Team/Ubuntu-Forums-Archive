---
title: "Beryl - No X close button on windows!"
date: 2007-05-03
forum: Desktop Effects &amp; Customization
---

### Post by jastonas on 2007-05-03
Hello guys, when I enable Beryl the minimize and close buttons disappear from all the windows!
To close a window i either have to right click in the taskbar or use alt+right click on a window!!
Anyone had the same problem? I checked the theme manager and it says that buttons are enabled.
I am usins beryl with nvidia-glx-new drivers.

---

### Post by ajgreeny on 2007-05-03
I had several similar problems when I first tried beryl in feisty kubuntu, with windows missing various elements and problems with the number of virtual desktops suddenly changing to 16 instead of my usual 4, but it suddenly started working OK for no reason that I could sort out, though it is possible that for other reasons I may have started a new session; I simply can't remember in detail.  However, I still find that there are too many uncertainties with beryl, so I don't run it by default, I just try it occasionally to see if things have changed for the better, or to show non linux users who belittle the system just what it can do.

---

### Post by jastonas on 2007-05-03
so i just have to wait?...:p
time will heal beryl...;p

---

### Post by curtistee on 2007-05-03
Is emerald running? Try this in a terminal window:

ps auxw | grep emerald

If all you see is something to the effect of

6768  0.0  0.0   2884   752 pts/0    R+   06:47   0:00 grep emerald

Run this:

emerald --replace

HTH,

Curtis

---

### Post by CRIMPS on 2007-05-03
I believe curtis is has a better answer than I do.  But a simple question to you would be:  What theme do you have selected in Emereld?  Some of the themes done have the window buttons, or they are hidden.

Dont know if thats much help.

Z

---

### Post by jastonas on 2007-05-03
well that didnt help:(
i even tried changing a theme and didnt notice any difference!
It seems that only some basicfunctions of beryl work only!

---

### Post by dmg025 on 2007-05-03
I have the same problems are you do.  initially after my install, beryl worked fine, but when i started messing around with the desktop effects option built into Ubuntu and then switched it back to my original settings, I lost all of my window buttons.  I now have no beryl effetcs and no window buttons.  Might just have to reinstall.  

Do you have a geforce 6800 by chance?  9755 drivers?

---

### Post by jastonas on 2007-05-03
the thing is that the buttons work fine with metacity manager, but when i enable beryl then they disappear.
I have an nvidia 7300 go (laptop)

---

### Post by ajgreeny on 2007-05-03
Quote from dmg025
"I now have no beryl effetcs and no window buttons.  Might just have to reinstall."

No you won't!  Just uninstall beryl for the time being using synaptic, or in terminal and restart.  I think the system will now start using the usual window manager instead of beryl, and you can go from there.

---

### Post by dmg025 on 2007-05-03
And then just reinstall beryl?  Beryl is 90% of the reason I use ubuntu over my windows

---

### Post by ronocdh on 2007-05-04
> **jastonas said:**
> the thing is that the buttons work fine with metacity manager, but when i enable beryl then they disappear.
I have an nvidia 7300 go (laptop)
dmg025: this works great. Just switch back to Metacity in the pull-down Beryl menu and you'll be all set. =) 3D effects won't be affected.

---

### Post by slambrick on 2007-05-04
I have just poted My fix forthis.
Under the  Beryl Icon Choose Advanced Beryl options then Rendering Path then change Automatic to Copy. this completely fixed mine
Cheers

---

### Post by dmg025 on 2007-05-04
Wow...why was that so simple?  I read so many threads and guides from people with the same problem.  Finally!  When something like that goes wrong I get so frustrated with my computer I sotp using now.  Now I can finally rest easy

Thanks again

---

### Post by Plasticman on 2007-05-05
> **slambrick said:**
> I have just poted My fix forthis.
Under the  Beryl Icon Choose Advanced Beryl options then Rendering Path then change Automatic to Copy. this completely fixed mine
Cheers

You sir are a saint. This worked straight away for me also after hours of playing around. 
Many thanks.

---

### Post by bokorpop on 2007-05-07
Ahh, I switched from Automatic to Copy and it didn't fix the problem for me.
Any more possible solutions? Beryl was a key factor in my switch to Ubuntu.

:confused:

---

### Post by bokorpop on 2007-05-07
I sopke too soon! I jsut solved my problem. Here is how I did it:
Click on the red gem and go to "beryl settings manager". Under visual effects choose "Window Decoration" and mark the checkbox. Thats it! Up and working!

---

### Post by Tazzy on 2007-05-11
Thanx slambrick!
Searched for days.  Worked great!  Even got my terminal window back.

---

### Post by chris242 on 2007-05-11
I'm new to ubuntu and beryl... but here is what i did to fix the problem.  Under Visual Effects go to 'blur effects' then 'Visibilty/performance'  and 'motion blur mode' it was set as 'fbo'... I changed it to simple. Fixed my problem at least, hope it helps who ever has this problem!

-chris

---

### Post by sowelie on 2007-05-11
Sounds like you guys are using a mix of beryl and the built in effects.  I would use one or the other as I don't think they work well together.

---

