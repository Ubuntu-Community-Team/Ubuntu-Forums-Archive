---
title: "Compiz settings ignored after update?"
date: 2011-10-13
forum: Desktop Environments
---

### Post by Myoldmopar on 2011-10-13
Greetings,

Enjoyed a nice upgrade to 11.10 this morning with no major problems.  I am sitting comfortably in Unity 3D and for the most part things are fine. 

However, I noticed that my launcher bar icons have reverted to their normal (large) size.  In 11.04 I had customized them down using CCSM without a bit of trouble.  I also started noticing that other compiz related tasks weren't working (ring switcher with super-tab, etc.).

I opened CCSM and noticed that all my effects were exactly as they were before, the icon size is down to 32, and other effects are enabled.  However, they appear to be ignored completely.

Is there a simple way to "flip the switch" to get them all working the way they were a few hours ago?

Thanks!  And cheers to the Ubuntu devs, it looks and feels great!

---

### Post by Myoldmopar on 2011-10-13
...and probably the thing I'd like to have back the most right now is the window snapping (maximize by dragging title to top, aero-style, whatever it is actually called...)

---

### Post by irv on 2011-10-13
I also did an update to 11.10 this morning and everything was working great, I went to change from the wall to the cube and my icons reverted back to large and I can get them small again. Another thing I can't get more then 2 desktop no matter how many I ask for. I set it a 4, and all I get is 2. I set it at 8 all I get is 2. I tried to got back to defaults and it won't even do that. I hope there is a simple fix for this?

---

### Post by irv on 2011-10-13
Since upgrading to 11.10, how do I know if I am running in 2D or 3D? And is there a way to switch back and forth? Maybe this is way Compiz setting are not working?

---

### Post by Myoldmopar on 2011-10-13
I found a reference on the web that if you able to move your launchers around in the unity bar (click and hold briefly then drag up and down to rearrange) then you are in 3D.  However, at the log-in screen I tried to log into 2D and it still allowed me to do that.  Some odd behavior here or a bad reference...

For reference to any other readers, I am running a Dell XPS 17, i7-2630, 8GB RAM, Nvidia GT555 3D, 64-bit 11.10.  An interesting note is if I go to the system info, it has a blank in the "graphics" entry.  It tells me my ram, processor, OS and disk space, but just blank on the graphics.  I am able to use the Nvidia control center to expand to dual monitors and adjust resolution, etc., perfectly...just as before.

---

### Post by Myoldmopar on 2011-10-13
On second thought...[This may help discern 2D vs 3D]("http://askubuntu.com/questions/62001/am-i-using-unity-or-unity-2d")

*Apparently* I have 2D enabled, because my launcher icons aren't folding, they are just scrolling.  Maybe once I get 3D in place, compiz will start working??  Or maybe I'm way off??  We'll see!! :P

---

### Post by Myoldmopar on 2011-10-14
Just to let any users out there know, I found the problem.  Even though the Nvidia settings manager was showing that it was using 285, there was still some problem.  I noticed there was a problem because in the *Additional Drivers* dialog, I wasn't able to activate any of them.  I then looked in the software center sources and found that it had disabled my x-swat ppa.  Thus, I guess it saw that the only video driver was 285-...-natty.  

Once I re-enabled this source, and did an update, it immediately found the 285-...-oneiric driver, rebooted, and bam, everything is great.  All compiz settings are in place and running strong!

Case Closed!

---

