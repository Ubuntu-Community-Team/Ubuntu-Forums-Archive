---
title: "CompizConfig Settings Manager"
date: 2014-11-19
forum: Desktop Environments
---

### Post by sami-mattila on 2014-11-19
For some reason I can set "Expo" to work without mouse click but not the "Scale".
Why is that and how can I fix it?

Sam

---

### Post by mc4man on 2014-11-19
While maybe someone will come along who knows what you're referring to you may want to be a little more verbose.
What does "to work without mouse click" mean?, ie. work how (keyboard binding, edge binding, whatever..

---

### Post by monkeybrain20122 on 2014-11-19
I think he means hot corners.

---

### Post by sami-mattila on 2014-11-20
Give the man a cigar :) @monkeybrain20122

---

### Post by mc4man on 2014-11-20
> **monkeybrain20122 said:**
> I think he means hot corners.

Well that works fine here for the 2 available initiates (window picker & window picker for all windows)
The initiate for *picker for window group* has been broken for several years & can only be done via dbus/command

I seem to remember you've had some hc issues so maybe you both are in same ballpark...

---

### Post by deadflowr on 2014-11-20
Now does it not work when you toggle it, or does it not work after you set it and login?
(Like somethings monkeybrain has(is?) fought with)

Unfortunately, I have no clue as to which version of Ubuntu...
I know it works fine for 12.04 and 14.04.
I don't have a regular Ubuntu 14.10 installed anywhere.
(only Kubuntu 14.10, which does not help in this case)

---

### Post by monkeybrain20122 on 2014-11-20
See if this helps (not really a fix, but a workaround which seems works well enough)
[http://ubuntuforums.org/showthread.php?t=2251650&p=13166747#post13166747](http://ubuntuforums.org/showthread.php?t=2251650&p=13166747#post13166747)

---

### Post by sami-mattila on 2014-11-21
For the moment upgrade does nothing for me since the Scale config still insist on the mouse click at the end. If I try to manually remove the <button1> from the end then the entire line resets.

---

### Post by mc4man on 2014-11-21
> **sami-mattila said:**
> For the moment upgrade does nothing for me since the Scale config still insist on the mouse click at the end. If I try to manually remove the <button1> from the end then the entire line resets.
Button is for mouse,  edge is for hot corner(s), example screen for initiate window picker on bottom right

---

### Post by monkeybrain20122 on 2014-11-21
> **sami-mattila said:**
> For the moment upgrade does nothing for me since the Scale config still insist on the mouse click at the end. If I try to manually remove the <button1> from the end then the entire line resets.

Did you try using the script to reset the corner on login?

Hi, **Mc4man**,

I noticed the colour of the theme in your screenshot.  I updated with your trusty-proposed ppa and got the same dull brownish  instead of orange colour, downgraded the ubuntu-theme package and it was  back to normal. Is it a bug?

---

### Post by mc4man on 2014-11-21
> **monkeybrain20122 said:**
> Did you try using the script to reset the corner on login?

Hi, **Mc4man**,

I noticed the colour of the theme in your screenshot.  I updated with your trusty-proposed ppa and got the same dull brownish  instead of orange colour, downgraded the ubuntu-theme package and it was  back to normal. Is it a bug?
No - that's what I want as fits my background. (onscreen & in life). Didn't imagine anyone else would use...

Some of the other packages there are also quite specific - 
unity is set for rotate so the expo icon will work on a 1x4 setting
compiz is patched to allow window picker for window group thru ctrl+alt+z 
nautilus has a boatload of personal patches.

(-I've moved both unity & compiz to the latest [here,]("https://launchpad.net/~mc3man/+archive/ubuntu/temp-for-diff2") but again contain personal changes, maybe I'll do generic builds if there is any interest in latest of both for 14.04...

---

### Post by monkeybrain20122 on 2014-11-21
> **mc4man said:**
> No - that's what I want as fits my background. (onscreen & in life). Didn't imagine anyone else would use...

Some of the other packages there are also quite specific - 
unity is set for rotate so the expo icon will work on a 1x4 setting
compiz is patched to allow window picker for window group thru ctrl+alt+z 
nautilus has a boatload of personal patches.

(-I've moved both unity & compiz to the latest [here,]("https://launchpad.net/~mc3man/+archive/ubuntu/temp-for-diff2") but again contain personal changes, maybe I'll do generic builds if there is any interest in latest of both for 14.04...

I see. I was updating some packages to see if they solve my problems such as show workplaces doesn't unexpose on click on unity > 7.20, but I have purged the ppa since.

---

