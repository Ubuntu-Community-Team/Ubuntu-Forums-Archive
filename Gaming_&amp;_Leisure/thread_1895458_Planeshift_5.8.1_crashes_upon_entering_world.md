---
title: "Planeshift 5.8.1 crashes upon entering world"
date: 2011-12-14
forum: Gaming &amp; Leisure
---

### Post by Daktyl198 on 2011-12-14
I have now tried to install Planeshift both system wide and not. When I installed it system wide, the updater failed to update any files. I'm pretty sure I know the reason for that (permission issues). When I installed it locally in my home folder everything works until I go to enter the server. I can choose my character and everything so I don't think its a problem with the client.

Is there a reason why it won't let me enter the world?

I have had Planeshift installed when I was using 10.04 and it worked fine. I'm using 11.10 at the moment.

EDIT: the version is actually 0.5.8.1, not 5.8.1

---

### Post by Perfect Storm on 2011-12-15
It's been awhile I played the game, but I think you need to run the updater first.

---

### Post by Dlambert on 2011-12-15
Try reinstalling following their strict directions.

---

### Post by Daktyl198 on 2011-12-15
I've tried both.
I already ran the updater (hence the version number being 0.x.x.1)

I have also tried reinstalling a number of different ways.
If i install it using sudo nautilus I have to login as root to update/play the game.
If I install it not in root, in my home folder, then I can't see any news and the updater does not automatically run.

Both ways crash after I choose my character.

---

### Post by Perfect Storm on 2011-12-15
Have you tried to run it through the game through the terminal to see the output when it crashes?

---

### Post by Daktyl198 on 2011-12-16
```
crystalspace.graphics3d.shader.fixed:
  Multitexture units: whopping 8
shader lighting_default_binalpha@@100: ....10%....20%....30%....40%....50%....60%....70%....80%....90%....100%
shader lighting_default_binalpha@@50: ....10%....20%....30%....40%....50%....60%....70%....80%....90%....100%
shader lighting_default_pvl_binalpha@@400: ....10%....20%....30%....40%....50%....60%....70%....80%....90%....100%
shader lighting_default_pvl_binalpha@@300: ....10%....20%....30%....40%....50%....60%....70%....80%....90%....100%
shader lighting_default_pvl_binalpha@@200: ....10%....20%....30%....40%....50%....60%....70%....80%....90%....100%
Killed

```
Those are the last few lines of code from the terminal. Everything before it looked fine besides a couple plugins failing to load. They were for external controllers though so Im not worried about those. It just kills the program after severely bogging down my computer for a few seconds

---

### Post by Perfect Storm on 2011-12-16
> **Daktyl198 said:**
> ```
crystalspace.graphics3d.shader.fixed:
  Multitexture units: whopping 8
shader lighting_default_binalpha@@100: ....10%....20%....30%....40%....50%....60%....70%....80%....90%....100%
shader lighting_default_binalpha@@50: ....10%....20%....30%....40%....50%....60%....70%....80%....90%....100%
shader lighting_default_pvl_binalpha@@400: ....10%....20%....30%....40%....50%....60%....70%....80%....90%....100%
shader lighting_default_pvl_binalpha@@300: ....10%....20%....30%....40%....50%....60%....70%....80%....90%....100%
shader lighting_default_pvl_binalpha@@200: ....10%....20%....30%....40%....50%....60%....70%....80%....90%....100%
Killed

```
Those are the last few lines of code from the terminal. Everything before it looked fine besides a couple plugins failing to load. They were for external controllers though so Im not worried about those. It just kills the program after severely bogging down my computer for a few seconds

Better to get in contact/use Planeshift forum to sort this out, IMO. Nothing much from the the output.

Have you checked if planeshift makes a log file of some sort?

---

### Post by Daktyl198 on 2011-12-16
There is an error log, It shows:
<src/common/paws/pawsimagedrawable.cpp:69 PreparePixmap SEVERE>
Could not open image: >/paws/base/maps/leather/bottom_right_1.png<
Could not open image: >Scaling Field Background<

Those 3 over and over. I might see the problem, but I haven't dappled in code enough to really know how to fix it.
Also, the Planeshift forums haven't been active since the middle of last year. Not even the admins have posted anything

---

### Post by Dlambert on 2011-12-16
Install OpenAL

---

### Post by Dlambert on 2011-12-16
Install Glibc. Are you using the latest ATI or Nvidia drivers?

---

### Post by Daktyl198 on 2011-12-16
OpenAL is installed.
I can't find Glibc...
and I have crappy intel graphics :(
But the sound and video worked perfectly fine through the tutorial, its just a problem with entering the "real" game.

---

### Post by Dlambert on 2011-12-16
> **Daktyl198 said:**
> OpenAL is installed.
I can't find Glibc...
and I have crappy intel graphics :(
But the sound and video worked perfectly fine through the tutorial, its just a problem with entering the "real" game.

I'm just posting other random post from other forums to try and help.

---

### Post by Dlambert on 2011-12-16
> **Dlambert said:**
> I'm just posting other random post from other forums to try and help.

[Install freeglut maybe? http://ubuntuforums.org/showthread.php?t=345177]("http://ubuntuforums.org/showthread.php?t=345177")

Just trying to help

---

### Post by Dlambert on 2011-12-16
What version of ubuntu are you running? Maybe try running at low detail, with unity 2d. Or of your running 64 bit, try running 64 bit, or 32.

---

### Post by Daktyl198 on 2011-12-17
The freeglut seems to be for people either using programs requiring it (Planeshift uses OpenGL, not that) or for people writing graphical programs.

Im on Ubuntu 11.10. I've turned down the detail anyways. Everything always auto-tunes to a slightly higher detail than my computer can do so its usually the first thing I do.

I haven't tried it in unity 2d yet. I don't really see how that would effect the game too much but i could try nonetheless.

---

### Post by Dlambert on 2011-12-17
> **Daktyl198 said:**
> The freeglut seems to be for people either using programs requiring it (Planeshift uses OpenGL, not that) or for people writing graphical programs.

Im on Ubuntu 11.10. I've turned down the detail anyways. Everything always auto-tunes to a slightly higher detail than my computer can do so its usually the first thing I do.

I haven't tried it in unity 2d yet. I don't really see how that would effect the game too much but i could try nonetheless.

Freeglut made me able to run cairo dock and WOW. So I would try it!

---

### Post by Daktyl198 on 2011-12-17
hmm. I think it did the trick! I can run it now... though it turned the sound off at first all I had to do was turn it back on. Its working good now.
Thanks for the advice. I still don't get WHY I would need freeglut, but hey: it works right?

I still need to have root privileges to run it but once again, it works at least.

---

### Post by Dlambert on 2011-12-19
> **Daktyl198 said:**
> hmm. I think it did the trick! I can run it now... though it turned the sound off at first all I had to do was turn it back on. Its working good now.
Thanks for the advice. I still don't get WHY I would need freeglut, but hey: it works right?

I still need to have root privileges to run it but once again, it works at least.

Yeah, I had to run as root too, it's weird. But freeglut is OpenGl libs/functionality. So it makes sense to me.

---

