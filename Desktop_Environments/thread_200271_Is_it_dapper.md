---
title: "Is it dapper?"
date: 2006-06-20
forum: Desktop Environments
---

### Post by iitywygms on 2006-06-20
A little story.  I blew up my install of ubuntu a few weeks ago.  So I had to reinstall, no big deal right?  Sorry, my last few weeks have been crazy.
When I first found ubunt I installed it on my laptop.  (Breezy) Had some issues with the wireless card. (Broadcom 4603) never got it to work.   So I purchased a prism card.  After some searching and reading I got it installed using ndiswrapper.  Great.  Worked well for 10 months. However, when it came time for a fresh install, the prism card was not recognized.  Okay, so i install the broadcom card and use it.
I tried the forum where you use the bcmfwcutter, (not sure if that is how it is spelled)  card would be seen, worked for a few minutes then slowed down and stopped working.  Okay, frustrated but not willing to quit.  Reinstall Dapper.  Follow a forum that uses ndiswrapper.  Works okay but sometimes it would not connect.  Hmmmm, try a new driver?  I uninstall the driver and try a new one.  Not recognized and hardware not present.  No big deal, just install the original driver.  Well when I tried that the driver that was working, it would not work. Not recognized and hardware not present.  Why? I dont know.
Have a few beers.....
Reinstall Dapper.  Use the fwcutter guide.  Seems to work.  But after a few reboots the ping times are hell.  Cant use the internet at all.
Drink more beer....
Reinstall Dapper, again
Decided that the best option for me was to use ndiswrapper.  I tried using the original driver that worked before.  Nope, hardware not present.  Same driver that worked before, but not this time.  So out of frustration i tried using the bcmwl5.sys driver.  Invalid of course, BUT, after I did that the driver I had would install.  Now that I have that figured out, I do another fresh install, (I had tried a bunch of differnt things and did not want to have a screwed up network)  Tried the ndiswrapper intall, could not install untill I tried the *.sys file.  After that the *.inf file installed.
Everything seems fine now.  The transfer rate in Windblows is a little faster but not by much.
Check out my post, I have had all kinds of issues.
So what is the moral of this story?  Was it me? did I do something wrong or is Dapper still buggy?  Dont get me wrong, I really like this distro.  Everything seems to work except wireless.  But if everyone has to do what I have, Ubuntu will never survive!

---

### Post by iitywygms on 2006-06-20
Crazy thing, now my internet speeds are faster than 
Windblows.  I hope things stay this way.

---

### Post by stanz on 2006-06-20
I'ld blame it on the brand of beer !  ;)

---

### Post by iitywygms on 2006-06-20
LOL.  I blame it on Broadcom.  Turned the laptop on this morning, no network.  Restart, boom it works.  I guess this calls for more beer! =D>

---

