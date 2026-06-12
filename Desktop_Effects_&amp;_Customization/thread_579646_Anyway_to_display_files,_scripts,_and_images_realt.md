---
title: "Anyway to display files, scripts, and images realtime on desktop?"
date: 2007-10-18
forum: Desktop Effects &amp; Customization
---

### Post by mithbuntu on 2007-10-18
Hi.

I have asked this question previously, but I asked in the wrong forum(noob chat), so I am going to ask in the correct one this time.

I would like to set up my nix desktop to look similar to my mac desktop. 
Here is a pic: [http://img137.imageshack.us/img137/3045/fullscreen1bq9.gif](http://img137.imageshack.us/img137/3045/fullscreen1bq9.gif)

My main question is... is there any possible way to display shell commmands (such as netstat or ps) realtime on my desktop(so i can see resource hogs/net connections)?
How about .log files that update (such as the red error text I have)?
Or images from computer/internet (in my image: real time air quality, upper level winds, weather, current cd track cd cover)?

I know I've seen it done before and I truly hope that my mac (which is nix based) can not outperform nix itself in this department.

Furthermore, I was wondering about setting up something on Beryl.  Is there anyway to load different backgrounds, desktop icons, etc on each desktop?  I'd like to set one up for my main programs, one for music/bkrnd apps, one for weather (meteorology major xD), and one for system status.

**BTW I am not looking for applets with static images here with text filled in. Those are ugly :(

---

### Post by mithbuntu on 2007-10-19
bump

---

### Post by mithbuntu on 2007-10-23
bump

---

### Post by serhito on 2007-12-15
did you figure out how to do it ? I am trying to display a current weather radar picture on the desktop.

---

### Post by john.nicholls on 2007-12-18
Log files that update:
In /var/log directory, type ```
tail -f syslog
``` (or whatever other log file you want).

---

### Post by sujoy on 2007-12-20
so, anyone found a way to display command outputs directly at the dekstop screen as shown in the screenshot? i guess it would be real cool and geeky. someone please, help us out...

---

### Post by sujoy on 2007-12-21
bump :)

anyway to even mimic it?

---

### Post by kaervos1024 on 2007-12-21
Assuming you are using Gnome, check out gDesklets. With a little python knowledge you should be able to modify an existing desklet to display whatever you want.

---

### Post by mithbuntu on 2008-02-25
No, I never found a way, sorry. :(

I gave up a while ago.  I guess geektool is just the best app for doing this on any OS.

I just figured since OSX is built on unix architecture, linux could handle it.

---

### Post by psyopper on 2008-02-25
Linux can handle it, and much more!

I highly recommend Conky from the repositories to do exactly what you are looking for.
```
sudo aptitude install conky
```

[There's a **huge** conky configuration thread right here]("http://ubuntuforums.org/showthread.php?t=281865") to answer darn near any questions you have about getting it set up. 

If you want something a little fancier there's gDesklets as mentioned above, or more to my preference, [Screenlets]("http://www.screenlets.org") that are very much like your Mac Widgets.

---

### Post by mithbuntu on 2008-02-25
I dont think conky can do images like I have on my mac... can it?

---

