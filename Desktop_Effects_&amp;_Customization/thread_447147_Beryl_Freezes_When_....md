---
title: "Beryl Freezes When ..."
date: 2007-05-17
forum: Desktop Effects &amp; Customization
---

### Post by typhoongs on 2007-05-17
My beryl freezes when i scroll any programs' scrollbar (especially firefox cos i use firefox frequently), but freeze occurs at random times i mean generally in first hour it doesn't freeze if i scroll the scrollbars and after one hour it often happens.
 Does anybody having the same issue ? what can i do to solve this issue ? 
 Actually i tried a lot of thing to solve this nasty problem, ie i stopped all window effects (every effect except open and minimize), i stopped scale effect, and some effects like them
 My system is : Nvidia GeForce go 7400, 8776 driver version, xorg 7.1.1, beryl 0.2

---

### Post by Ch33zm0ng3r on 2007-05-20
I have a similar problem.  My system hangs for about two - three seconds every time I close or minimize a window when running Beryl as my window manager.  I'm just chalking it up to the fact that Beryl is still considered unstable.

---

### Post by Tarsonis on 2007-06-04
What exactly does a characteristic Beryl freeze look like?  I believe I'm having the same issue (firefox and other programs freezing on rapid scroll) but the mouse is still moveable.  Once the freeze happens I can't even ctrl-alt-backspace.  Is this what others are seeing as well?

---

### Post by borahshadow on 2007-06-04
I see this too I can't even ctrl-alt-backspace 
I was doing quite a few things I didn't pin it to when I scroll but I just experienced one of these lockups and now that I think about it I was scrollong when It happened 
and It was about 1 hour since I had (re)loaded beryl 

I have rendering part to copy to reduce the black window bug if everyone could postweather they have any settings like that on anything but auto mabey we can pin it down better

ps My windows sometimes hang for 2-3 seconds too kinda annoying I love beryl effects but bugs might make me use it only when I want to show off to family and friends :(

---

### Post by robertpolson on 2007-06-05
I have the same problem. Beryl freezes but I can still move the mouse, but nothing else works.

Nvidia GO 7700 Asus G1 Laptop

---

### Post by borahshadow on 2007-06-05
I just experienced another one of these lockups when coming out of screen saver hmmm. (I was using the kde fireworks screensaver which will sometimes hang temporally while I have beryl on but thistime it triggered one of these total system freezes)

---

### Post by laramarvin on 2007-06-12
Have any of you tried with an older (and more stable) version of Beryl?

---

### Post by borahshadow on 2007-06-13
I have not tried an older version would it realy be more stable?

---

### Post by robertpolson on 2007-06-13
I went to Beryl general settings and unchecked "Sync to VBlank" no idea what it is, but so far no freezes.

Also, another problem I have is that the screen flickers for less then a seconds like every 30 seconds or so. I had this before. Any ideas ?

Edit: See if this can help anyone: sudo apt-get install nvidia-glx-new
 
The flickering is gone now, lets see if I get any freezes.

---

### Post by logic7 on 2007-06-21
> **Ch33zm0ng3r said:**
> I have a similar problem.  My system hangs for about two - three seconds every time I close or minimize a window when running Beryl as my window manager.  I'm just chalking it up to the fact that Beryl is still considered unstable.

I've had the same annoying problem, it seems that the automatic thumbnail generation under Beryl Settings Manager/General Options/Window Thumbnails is causing this. Smaller Thumbs = Less delay or turn them off completely. Hope that helps :)

---

### Post by zero244 on 2007-06-21
I had the same problem it would freeze and I could move the mouse but nothing else.
I switched my server to XGL and reinstalled Beryl and have had very few problems since. All the features run though I have some of them turned off.
If you run Beryl in terminal and anything shows as failed, Beryl is not going to work for you unless you run it with XGL.

---

### Post by warreng on 2007-06-21
I've got this issue too - Beryl (and Compiz) lock anywhere between 2 and 30 seconds in to a session.

How do you go about using XGL?

---

### Post by zero244 on 2007-06-21
I will try to post a link to a how to for XGL.
You can do a search.....look for a how to that fits your version of Ubuntu and your video card type. It is pretty easy to setup a XGL session.
I copied and pasted a script that allows me to use XGL or not to use it.
Im using a Nvidia 7600 card and tried everything to get beryl running.......it would freeze me solid like you in about one minute or less. Ive been running beryl with XGL and havent had only one freeze and I think it was Firefox that froze me.
I think beryl......and some of the html code using firefox causes problems sometimes.
I hope you can get Beryl or Compiz working. It is pretty impressive.

---

### Post by prince_niceguy on 2007-07-09
> **borahshadow said:**
> I just experienced another one of these lockups when coming out of screen saver hmmm. (I was using the kde fireworks screensaver which will sometimes hang temporally while I have beryl on but thistime it triggered one of these total system freezes)

I too have this problem when I return and screen saver has started. I am using my images folder as the scren saver... any resolution so far???

---

### Post by backcracker on 2007-09-30
I've had the same annoying problem, it seems that the automatic thumbnail generation under Beryl Settings Manager/General Options/Window Thumbnails is causing this. Smaller Thumbs = Less delay or turn them off completely.

WORKED! thanks~

---

### Post by backcracker on 2007-10-05
Hmmm,
didn't work...... :-(

---

