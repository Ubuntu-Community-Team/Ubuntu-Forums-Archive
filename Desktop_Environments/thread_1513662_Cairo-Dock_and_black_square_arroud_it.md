---
title: "Cairo-Dock and black square arroud it"
date: 2010-06-19
forum: Desktop Environments
---

### Post by Plexis on 2010-06-19
Hi m8, 

I am running for some time Ubuntu 10.04, and I decied to install Cairo-Dock to make my notebook more look like Mac OS ....

But I have strange if I can call it problem. It is black squate surrounding Cairo-Dock. I tryed to change backgroud to black but still when i am on some application and Cairo-Dock appear i see it.

I also uploaded screenshoot of my desktop so If somebody had before same "problem" , maybe he can help me to solve it.

I am running **no OpenGL** Cairo-Dock.

Thanks to all of You for help.

---

### Post by Brandel Valico on 2010-06-19
You need to install a compisitor. The default Gnome doesn't do so. Try installing Compiz it has a built in one and will get rid of that black square.

---

### Post by Plexis on 2010-06-19
I am so sorry, i found out how to do it :

```
**I have a black background around my dock.**
**Tip:** If you have an ATI or an Intel card, you  should try without OpenGL first, because their drivers are not yet  perfect. 
You need to turn on compositing. For instance, you can run Compiz or  xcompmgr.  
If you're using XFCE or KDE, you can just enable compositing in the  window manager options. 
If you're using Gnome, you can enable it in Metacity in this way : 
 Open gconf-editor, edit the key  '/apps/metacity/general/compositing_manager' and set it to 'true'. 
```

My notebook is Toshoba Satellite Pro U500 with nVidia Geforce 210 CUDA , and already running nVidia driver which ubuntu sugested to me, but somehow i needed to do this to get it working.

Thanks to all.

---

### Post by Brandel Valico on 2010-06-19
No worries nice to see you got it working. Also nice to see I was wrong and there is a way to get it going in Meticity. 

I enjoy any day I learn something new.

Be sure to mark the thread "Solved" when you get a chance.

---

### Post by pechan98 on 2010-06-29
Great Work :D Thanks for your help :D

---

### Post by sleepee on 2010-08-22
Thanks for this thread.
I was having the same issue and changing the gconf-editor option worked for me.

---

### Post by dvessels on 2011-02-05
:guitar:):PI too am having the problem of the black background around my cairo-dock. I also tried opening the gconf-editor, but I'm afraid my results were not quite the same. As a matter of fact, there was no change at all. Very disappointing. Does anyone else have any ideas? BTW, when I went to try the Compiz manager, it did not look like the one in the example.

Confused (as usual)

---

### Post by Copper Bezel on 2011-02-05
If the Metacity compositing didn't work and you want to switch to Compiz, you don't actually have to install ccsm, although you'll most likely want it. What example did it not look like?

For now, just go to Appearance Preferences and select the Visual Effects tab, then select "normal." You'll switch to Compiz's composited window manager. Alternately, run compiz --replace from the Alt+F2 Run Dialog.

---

### Post by Cathhsmom on 2011-02-05
I have had this happen to me.  I fixed mine by changing my visual effects to Extra.  Somehow, my visual effects  got set to none, and behold, I get a black box around my Cairo Dock.  But changing the visual effects to Extra, the black box disappeared.

---

### Post by Cavsfan on 2012-03-15
> **Plexis said:**
> I am so sorry, i found out how to do it :

```
**I have a black background around my dock.**
**Tip:** If you have an ATI or an Intel card, you  should try without OpenGL first, because their drivers are not yet  perfect. 
You need to turn on compositing. For instance, you can run Compiz or  xcompmgr.  
If you're using XFCE or KDE, you can just enable compositing in the  window manager options. 
If you're using Gnome, you can enable it in Metacity in this way : 
 Open gconf-editor, edit the key  '/apps/metacity/general/compositing_manager' and set it to 'true'. 
```My notebook is Toshoba Satellite Pro U500 with nVidia Geforce 210 CUDA , and already running nVidia driver which ubuntu sugested to me, but somehow i needed to do this to get it working.

Thanks to all.

After today's update for Lucid, I rebooted and only had a black screen with no cairo dock.
I did as mentioned above and it allows cairo dock to run without open gl. But, open gl mode 
still won't do anything except display a weird rectangular box at the bottom left - no icons.

---

