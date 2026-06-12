---
title: "Some random Beryl questions - one minor mishap.."
date: 2007-06-06
forum: Desktop Effects &amp; Customization
---

### Post by detroit/zero on 2007-06-06
Well, my first quetion is the rather important one, but should also be the easiest to answer, so I'll jump right into it:

**1.** On the Beryl Manager, there's the Advanced Options menu. I was fiddling with things and under the Rendering platform sub-menu, I accidentally switched the selection from 'Force NVidia' to 'ForceXGL'. Now my desktop freezes when loading. Where might someone as foolish as myself go about finding that setting and changing it back? Even if I could just set Metacity as the window manager, I think that would at least get me to where I could alter the settings right on that computer. I don't have GUI on that machine, but the command line is still fine, of course. I can also SSH or VNC into it from my laptop and do it that way. In any event, I'm just unsure where to start looking.. 

**2.** I had Beryl up and running like a champ. A 3GHz processor and an NVidia GeForce FX 5500 gave me pretty much all the eye-candy options I wanted running at 75FPS. About a week ago I started playing with Emerald themes and got everything looking just the way I wanted it. It still runs great with one minor exception: Whenever I'm using Swiftfox and I go into Yahoo Games (a Java applet) it bogs the system down pretty heavy and everything gets all herky-jerky on me (goes down to about 20 FPS with roughly 75% processor activity heavy on the I/O wait time). If I select Metacity as the window manager, it runs smooth as silk.. once I put Beryl back in charge, it loads down and runs like crap. Any thoughts on that? 

(I only mention it as being connected to my fiddling with the Emerald Themer because that's when the problem seems to have started. Before I used any Emerald theme, the Java applets would run inside Fire/Swiftfox with no problems and barely any noticable excess processor activity. Switching over to Heliodor has a minor effect and boosts me up to about 45/50 FPS but it's still weighted down. Also, since using Emerald, I notice all the animation I use in Beryl are more jittery than they used to be.)

That's not even really all that important.. more about convenience than anything. It gets to be a pain switching to plain-Jane Metacity to play Pool when you're used to haveng a flashy desktop.  

Anyhoo, thanks for any help you can offer.

---

### Post by detroit/zero on 2007-06-07
Problem #1 has been solved. After digging and digging trying to find the file that held that setting and coming up empty handed, another goof saved me.

I was using my laptop to SSH into my desktop and search around. Somewhere along the line I logged out of my laptop, and tried sometthing different. I logged into my desktop using the XDMCP option from the login-screen. Metacity was selected as the default window manager for the remote login, and I was able to make the modifications.

Now.. anyone with any opinions on problem #2? There's no valid reason I can think of that a 3GHz processor and a halfway decent NVidia card should get bogged down by Java applets and Beryl animations..

---

