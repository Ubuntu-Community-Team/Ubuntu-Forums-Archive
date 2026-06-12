---
title: "Wine, WoW, and Beryl"
date: 2006-12-14
forum: Gaming &amp; Leisure
---

### Post by Vord on 2006-12-14
So, earlier today, I installed Beryl on 6.06, and I have to say, it's gorgeous. Only problem is, whenever I try to start WoW in opengl mode, I get screen flickers to hell, and it finally pops up a box after some laboring that says "Unable to start 3d acceleration." Any idea how I can fix this?

---

### Post by Shatrat on 2006-12-14
I just turn off Beryl before launching WoW.
You can right click on the beryl panel icon and use Select Window Manager to use Metacity while playing 3D games.

---

### Post by Vord on 2006-12-14
Oh, cool, I'll just do that from now on, thanks.

---

### Post by Vord on 2006-12-14
Okay, well, I switched to metacity, and it's still telling me "Unable to start 3D acceleration"

It still works fine in direct 3d, though...

---

### Post by hikaricore on 2006-12-15
I get that error when attempt to run wow with X in 16bit colour.

Is your X session running in 24bit or 16bit colour?

---

### Post by Vord on 2006-12-15
I can't remember how to check. Enlighten me?

---

### Post by Vord on 2006-12-15
okay, well I did cat /etc/X11/xorg.conf | grep DefaultDepth and it output as running at 24-bit depth. Any other ideas?

---

### Post by Vord on 2006-12-15
So no one has any clue what the hell?

---

### Post by reiki on 2006-12-15
What nVidia drivers are you using?
In Edgy (I won't install Beryl on my Dapper installation), I installed Beryl and it was really simple. I'm using the 9629 nVidia drivers I think. AIGLX so no extra X stuff was necessary. 

I can start WoW with Beryl running and all it does is cut my framerate (about in half). 

To be honest, while Beryl is cool and all that, I left if out of my Dapper install because it doesn't really do anything significantly helpful for me as far as how I use my computer. It's eye candy.

In Edgy, it's still installed but I rarely ever start it. It's very cool, but it's just a toy and if it adversely affects the way programs run, then I can do without it. Beryl is making advances pretty rapidly and I expect it will be more forgiving in the near future, but for now I can live without it.

My advice is that you make a choice. Beryl or WoW. OR..... install another hard drive, install Edgy, and have a bit of fun.

Again... if WoW is a big deal, then you need to decide if Beryl is more important than WoW or the other way around. There are probably ways to get it working the way you want on Dapper (I think there's a script that stops Beryl to run WoW and then turns it back on after you're done playing, but I think even THAT can have some issues).

---

### Post by Naegling23 on 2006-12-15
I love beryl, and wow, but you can have both.  Wow wont run properly with beryl running.  Something about fullscreen programs in beryl.  Mythtv and wine do not run properly.  I find that switching off of beryl works fine though.  One question though.  What are you using to run beryl on.  If it is AIGLx, then your fine, if its XGL, then thats your problem, because XGL will not be able to run most 3d games.

---

### Post by superm1 on 2006-12-15
> **Naegling23 said:**
> I love beryl, and wow, but you can have both.  Wow wont run properly with beryl running.  Something about fullscreen programs in beryl.  Mythtv and wine do not run properly.  I find that switching off of beryl works fine though.  One question though.  What are you using to run beryl on.  If it is AIGLx, then your fine, if its XGL, then thats your problem, because XGL will not be able to run most 3d games.
MythTV generally won't run *in* Xgl.  If your running Xgl, its best to run myth on display :0 instead of :1 (u get Xv acceleration).  If your running Aiglx (or native nvidia for that matter), then you **shouldn't** have too many troubles.

---

### Post by Naegling23 on 2006-12-15
> **superm1 said:**
> MythTV generally won't run *in* Xgl.  If your running Xgl, its best to run myth on display :0 instead of :1 (u get Xv acceleration).  If your running Aiglx (or native nvidia for that matter), then you **shouldn't** have too many troubles.

I dont run mythtv in xgl.  I use beryl in aiglx.  Mythtv runs, but it doesnt do fullscreen.  Im aware that it does not work in xgl, a lot of things dont.

---

