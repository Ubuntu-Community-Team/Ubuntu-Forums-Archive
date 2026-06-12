---
title: "Google Earth woes?"
date: 2009-01-26
forum: General Help
---

### Post by fINTiP on 2009-01-26
I've got an ATI radeon 7200, if I'm not mistaken (it's been a while since I dealt with it), and I believe I'm using the proprietary drivers--again, it's been a while since I dealt with that.

I was running compiz initially, but I get an almost identical failure when running it in metacity.

So the problem:

I installed google earth with the package manager, (it gave me 4.2.something, I'm fairly sure), and tried to start it up.

I get the splash, and then the program loads, I get an initializing popup, (I think that's what it's saying, it has to do with loading), and then I get the "tip of the day". The globe actually loads, and begins spinning, loading. 

And then it crashes. Maybe 10 seconds altogether.

With compiz, the two or three windows that GE loads were glitching out with each other. Without compiz, the windows don't glitch out themselves. Crashing works exactly the same in both cases though.

Googling hasn't shown me anyone with quite my problem.

Any ideas what's going on? Any more data I can provide that would be helpful in providing a diagnosis?

---

### Post by Roasted on 2009-01-26
Due to Google Earth 4.3 looking like absolute garbage with the type of font used, I uninstalled it to go to 4.2. I was also downgrading to 4.2 to hope that 4.2 is more stable because 4.3 crashes if I use F11 to fullscreen at random times.

However, I ran into the same thing with 4.2. It opens, but before you can type in what you want, it crashes.

I won't lie, I have no idea what it is. I'm just posting here so you know you're not alone.

I am, however, running 64 bit Ubuntu 8.10. I wonder if 64 bit support lacked with 4.2 and is supported in 4.3. Or... something?

Edit - I just decided to put in 4.3. It's more stable from what I can see. I also noticed that if you remove the sidebar, it's pretty much full screen, so that'll take away from my F11 problem.

I suggest you install 4.3 and give that a shot. It's in synaptic. Also, if you have a problem with the font like I did, you can do this... 

Edit ~/.config/Google/GoogleEarthPlus.conf


In [Render]

Change the line:

GuiFontSize=8

to

GuiFontSize=14

If that doesn't work, you can do what I did... I left my font size 8, but I added this line...

GuiFontFamily=Arial

If these lines don't exist, you can add them. I had to add them. Now Google Earth 4.3 looks fine to me!

---

