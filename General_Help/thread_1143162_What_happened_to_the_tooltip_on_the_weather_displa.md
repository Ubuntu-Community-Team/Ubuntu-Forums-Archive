---
title: "What happened to the tooltip on the weather display?"
date: 2009-04-29
forum: General Help
---

### Post by Woody1987 on 2009-04-29
The clock has an option to display the current temperature and weather. In intrepid i could hover my mouse over this and it would display the wind speed, what it feels like and tomorrows temps. In jaunty, this no longer appears. What is going on?

---

### Post by aniruddha on 2009-04-29
That's strange. I still seem to retain this function.

---

### Post by wyth on 2009-05-03
Lucky you.  I lost all weather functions completely.  I can turn the weather on in the clock applet, but nothing shows whatsoever.  I can add the weather applet, but it's always blank.  This only happens on my desktop, not my laptop.

The only bug I've found about this is for a specific Spanish location not updating.  

Something seems to be up with the weather applets.

---

### Post by cariboo on 2009-05-03
Click on the clock and make sure the location is set. Click on the arrow beside Location, Make sure the location is correct and click the set button on the right side. THis should get the Weather applet working correctly.

---

### Post by wyth on 2009-05-03
> **cariboo907 said:**
> Click on the clock and make sure the location is set. Click on the arrow beside Location, Make sure the location is correct and click the set button on the right side. THis should get the Weather applet working correctly.

Was that directed at me?  If so, my location is set, but it just doesn't give me any weather.

---

### Post by fewyun on 2009-05-03
I just had the same issue. It was stuck at a past weather setting and provided no tooltip. I fixed it using the suggestion above -- specifically: Go to the right side of your location in the menu next to the location that you want and click "set." That will set it to be the primary location and provide weather. It must have lost the primary location setting when I was deleting other locations.

But it seems that when it loses the primary location it should also remove the weather to make it less confusing than a permanently stuck weather forecast.

---

### Post by timzak on 2009-05-05
I'm having the same problem and the tip above did not work for me.  I have two locations, and tried setting them both as "Home" and no matter what, weather details do not pop up when I mouse over the two locations like they used to in Hardy.

---

### Post by Sarai the Geek on 2009-05-05
I had this problem when I upgraded to Jaunty from Intrepid- mousing over the weather button just brought up the same thing that popped up when mousing over the time. I ended up (for other reasons) doing a fresh install and now it works. Weird.

---

### Post by timzak on 2009-05-12
If anyone is interested, I found what causes this bug to show, at least on my system.  Right-click on the clock, select Preferences, and enable "Show seconds".  This will cause the weather tooltips to stop working in the clock applet.  Turning off "Show seconds" allows the tooltips to work once more.

Hope this helps someone.  I've reported it to Launchpad already.

---

### Post by wyth on 2009-05-12
I still can't get the weather to show anything.  It works on my wife's account, and it works on my laptop, just not my desktop account.  I'd rather find out what's wrong than create a new account, but I'm thinking of testing out a 64 bit install anyway.

---

### Post by timzak on 2009-05-12
Might want to play with some of the other settings in clock preferences to see if they have any effect.  I was stunned that disabling the seconds fixed it for me.  If something that random will fix it, something equally random might work for you.  The seconds is a modification I always make to my clock applet, so I didn't even recall that it was non-standard.  Is there anything you change in the clock applet besides seconds?  Maybe 12hr/24hr setting?  Check it out.

I'd recommend checking out the 64-bit version regardless.  I've gone back to 64-bit in Jaunty for the first time since Gutsy and for the first time, I don't have to jump through any hoops.  All of my apps work out of the box, including Flash and Java.  Back in Gutsy, I remember having to follow howto's to hack Flash and Java to work, and there were some other apps that weren't available in 64-bit versions.  For the first time, I'm completely satisfied with a 64-bit OS.  Hopefully it works for you too.

---

