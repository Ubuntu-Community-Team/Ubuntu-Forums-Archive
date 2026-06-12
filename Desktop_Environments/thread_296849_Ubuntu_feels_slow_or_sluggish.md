---
title: "Ubuntu feels slow or sluggish"
date: 2006-11-10
forum: Desktop Environments
---

### Post by gGh on 2006-11-10
I was recently recommended Ubuntu (edgy) by a friend and I really like it. However, it feels rather slow or sluggish.  For example when I focus rythmbox I can see it "being drawn". Or when i just drag around a console window over a firefox window, CPU usage goes up to about 60-70% and I see the window lagging behind a little bit.

I am running it on a P3 1.8GHz, 512MB RAM and a GeForce 3 ti 200 64MB and have installed the nvidia drivers (nvidia-glx). I have tried checking around on the forum for a solution and tried running dpkg-reconfigure xserver-xorg, but it didn't change anything. Other than that I haven't found any other usefull information.

I might also mention that when I tried Kubuntu I didn't notice any of the same problems. I have now gone back to Ubuntu since i prefer it.

Does anyone know what might be wrong?

---

### Post by 23meg on 2006-11-10
X is known to be slow in window drawing and resizing operations. OpenGL-based accelerated X will remedy this in the near future. You can already use Beryl or Compiz in a composited environment to get better 2D performance. 

Check [this]("http://www.ubuntuforums.org/showpost.php?p=1114025&postcount=31") out for some possible remedies.

---

### Post by gGh on 2006-11-10
Thanks for the quick reply, I'll check compiz/beryl out when I get home today.

---

### Post by hoodwink on 2006-11-11
> **gGh said:**
> I was recently recommended Ubuntu (edgy) by a friend and I really like it. However, it feels rather slow or sluggish.  For example when I focus rythmbox I can see it "being drawn". Or when i just drag around a console window over a firefox window, CPU usage goes up to about 60-70% and I see the window lagging behind a little bit.

I am running it on a P3 1.8GHz, 512MB RAM and a GeForce 3 ti 200 64MB and have installed the nvidia drivers (nvidia-glx). I have tried checking around on the forum for a solution and tried running dpkg-reconfigure xserver-xorg, but it didn't change anything. Other than that I haven't found any other usefull information.

I might also mention that when I tried Kubuntu I didn't notice any of the same problems. I have now gone back to Ubuntu since i prefer it.

Does anyone know what might be wrong?

Probably a combination of cpu speed and memory. I'm running an AMD64-3400+ (32bit mode) with 1g memory on Kubuntu with an nVidia card. If I drag a Konsole screen around the desktop, there is no hesitation, delay, or ghosting in redrawing the screen, but cpu utilization does climb to about 50%.

---

### Post by Cl1mh4224rd on 2006-11-12
*sigh* I've had this problem with every Ubuntu release I've tried.

CPU: AthlonXP 2700+
Video: Radeon X800GTO (Radeon 9800PRO previously)
MB: Asus A7N8X Deluxe
RAM: 1GB Corsair XMS (2x512MB, dual-channel)

I had installed the proprietary ATI drivers. No luck. I even installed XGL and Compiz/Beryl. No luck. Recently I had wondered if it may be poor or missing motherboard drivers, but after reading this thread, I guess not.

That's extremely disappointing. I find games at 30FPS or lower on Windows to be an almost nauseating slideshow, so watching windows draw is an unbearable annoyance to me.

Looks like I have to check back in another 5 years. :(

---

### Post by 23meg on 2006-11-12
> Looks like I have to check back in another 5 years.In the worst case, check back in a year or so, when OpenGL-based accelerated X will have matured a lot.
> *sigh* I've had this problem with every Ubuntu release I've tried.
I too have had it with every release, but partial remedies, along with a few forced changes in my working habits, and finally Beryl, have got me through. 

Do you see windows redrawing with Beryl? With what settings? What's in your xorg.conf? Can you send some screen captures if that's not too hard? I'm really enthusiastic about solving (even if partially) this particular problem for different people with different configurations.

---

### Post by Cl1mh4224rd on 2006-11-15
> **23meg said:**
> . . .along with a few forced changes in my working habits. . .
Can you say those changes were for the better as far as productivity goes, or were they merely to avoid this issue?

> Do you see windows redrawing with Beryl?
I had Beryl running on Dapper, but I recently installed Edgy (again). The last time I tried installing XGL+Beryl on Edgy, things didn't go so well. In fact, I've had a hell of time with XGL+Beryl in general, too (but that's another thread, which I think I'll either search for or start soon).

But to answer your question, yes, I'm still aware of the drawing. It's still painfully noticeable with Firefox. It's always been the most outrageous offender for me (XUL's neat, but man... :|).

> With what settings? What's in your xorg.conf? Can you send some screen captures if that's not too hard?
I don't know what settings at the moment. I'll see if I can get XGL+Beryl working in Edgy here and get back to you.

---

