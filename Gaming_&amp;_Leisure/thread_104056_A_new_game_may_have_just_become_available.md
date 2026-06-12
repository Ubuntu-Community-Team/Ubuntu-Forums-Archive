---
title: "A new game may have just become available"
date: 2005-12-15
forum: Gaming &amp; Leisure
---

### Post by Gastric ReFlux on 2005-12-15
I'm a recent returner to using Linux, and one area of interest for me has been the apparent improvements in Wine since I had last used Linux in 2001/02.  Now one of my favorite games for PC's is the Out of the Park baseball series, and I've sometimes seen people on those forums talking about trying to get Out of the Park, or OOTP, running under Linux.  

Now that I had returned earlier this week, and installed a Linux partition on my hard drive, I was beginning to explore how to get OOTP working in Linux, most especially the Elicense wrapper which is used by OOTP as their means of ensuring payment for their product.

But now this morning, OOTP announced that OOTP5, the version which was released in 2003, is now available for free download and you can run it without Elicense.

[http://www.ootpdevelopments.com/article.php?newsid=396](http://www.ootpdevelopments.com/article.php?newsid=396) is a link to the official announcement.

[http://ootpdevelopments.com/board/showthread.php?t=107856](http://ootpdevelopments.com/board/showthread.php?t=107856) is a link to a thread in their forums where the programmer has stated it's without any Elicense.

So later when I get home I'm going to see about installing it to run under Wine.

It's not a fancy graphical baseball simulator, but a text sim, and is well regarded for its statistical accuracy and ability to customize.

If anyone gets a chance to try it, I recommend it.  I'll further add if someone gets a chance to try installing it in Linux, and discovers any potential trouble areas or tweaks that need to be done, I'd appreciate it as I'm still relatively new to trying to get Windows programs running in Wine.

---

### Post by Gastric ReFlux on 2005-12-15
No baseball fans here, maybe?  

Anyhow, I have managed to get OOTP5 to load using Wine.  Unfortunately, I seem to be having a severe performance problem with it, as it is very very slow in reading and accessin the hard drive.  And that's bad because as a game that tracks a whole lot of stats, it does a lot of writing and reading of the drive.

Plus, the interface is very slow and not responsive.  When starting it, I get a couple of messages in the terminal:

fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fe1bda0)->(00010022,00000008)
fixme:ddraw:DIB_DirectDrawSurface_Blt dwFlags DDBLT_WAIT and/or DDBLT_ASYNC: can't handle right now

I don't know if anyone has any insight regarding those.  Also, and this is really annoying, once it starts, OOTP's window insists on being on top of everything and everywhere.  I started it on my 2nd desktop, and when I would go to the first, or third, or fourth, the OOTP window would be on top.  Is there any way to stop it? Then I could at least use the internet to read the winehq manual and such.

Any help here would be appreciated.  I would really love it if I could get this game to run smoothly in Linux.

---

### Post by Gastric ReFlux on 2005-12-15
Okay, I figured out how to stop it from following me switching from desktop to desktop, I used winecfg to get it to emulate a virtual desktop and that keeps it in place.  I also disabled sound while I was at it, since this game doesn't need sound really.

Still, it's freaking slow compared to it in Windows.

---

### Post by Gastric ReFlux on 2005-12-15
Okay, I've also observed that a process called Xorg gets heavy cpu usage when trying to run OOTP5.  I'm guessing that's related to the graphics and X Windowing system.

---

### Post by rykel on 2005-12-15
hey, though i am not playing the game, but i must thank you for posting your results here!  you never know, but one day some OOTP fan using linux will come across this thread and appreciate you for starting it. cheers!

---

### Post by Gastric ReFlux on 2005-12-15
Here's even a couple of screenshots from my attempts earlier.

[IMG]http://i4.photobucket.com/albums/y147/xulfercirtsag/load.jpg[/IMG]

[IMG]http://i4.photobucket.com/albums/y147/xulfercirtsag/exhibit.jpg[/IMG]

The first one shows the initial loading screen, which was taking forever in my first try.  And hard drive access, reading/writing is horribly slow.  

The second screenie was from me patiently clicking and waiting for the game to respond to get me into an exhibition game.

---

### Post by rykel on 2005-12-15
man, and i thought u said it was a text sim (i assumed text-based) game... hehe, it's pretty graphical!!

---

### Post by Gastric ReFlux on 2005-12-16
[QUOTE=rykel]man, and i thought u said it was a text sim (i assumed text-based) game... hehe, it's pretty graphical!![/QUOTE]

Yeah, it is text-based, don't get fooled by my wallpaper in the background.  When you play a game in it, it'll display a field and then where you can see the pitcher and batter ratings/stats, when you click on continue that's where the text commentary is displayed to tell you the result of the play.  

Anyhow, I just had a flash of insight this morning.  I've seen others here talk about installing the Nvidia drivers for their video cards, and that they work much better. I'm wondering if I do that, will it possibly improve my performance with the system handling the DirectX that OOTP uses?

I think I'll give those a go when I get home tonight.

---

### Post by Gastric ReFlux on 2005-12-16
Crud.  Now I'm not so certain that grabbing the Nvidia drivers will fix the problem, as I've been searching and reading through threads where many are describing an issue with the Xorg process and problems with 2D rendering and Nvidia video cards. 

Of course, I do have that old ATI Rage card that might be worth plugging in.  

But reading through the stuff has nearly convinced it is the issue with Xorg that is making the game incredibly slow.  If I solve that, I believe the issue where it is writing and reading from the hard drive would be solved.  

So I basically know what is on my plate to try this evening.

---

### Post by Gastric ReFlux on 2005-12-16
I followed Method 1 in this thread:

[http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)

And that seems to have worked to solve my runaway Xorg process problem.  OOTP doesn't run as fast as it does natively in Windows, but I would say it's workable now.

It has some weird glitch where results of formulas for batting averages, ERA, and winning percentage result in numbers looking like this:

An ERA that should be 4.50 looks like 4..50+e00

A batting average that should be .182, the batter has 2 hits in 11 at bats, shows up as 1..818e-01

---

### Post by rykel on 2005-12-18
[QUOTE=Gastric ReFlux]I've seen others here talk about installing the Nvidia drivers for their video cards, and that they work much better. I'm wondering if I do that, will it possibly improve my performance with the system handling the DirectX that OOTP uses?

I think I'll give those a go when I get home tonight.[/QUOTE]

hey, to install the official nvidia driver (version 7667), simply enable the Universe and Multiverse repositories in Synaptic Package Manager.

Next, download and install nvidia-glx and whatever additional files it might ask for.

Then, in a terminal, type: **sudo nvidia-glx-config enable**.

hope tat helps!!!

tat should do the trick, and you'll have 3D enabled.

to tweak your nvidia driver after installation, you can type the following in a terminal: **nvidia-settings**.

---

