---
title: "Opera browser freezes then resumes on some sites?"
date: 2012-07-25
forum: Desktop Environments
---

### Post by cybrsaylr on 2012-07-25
This has been happening for a couple weeks now.

 I use Opera 12.00 on my Dell posted below in my sig most of the time. Opera has been my fav browser for several years. I go to some sites and Opera will just freeze up, then a couple seconds later PC monitor screen will dim down some, then a few seconds later screen will brighten back up to normal and resume as if nothing happened. The sites vary from Yahoo to just about any other site visited. In the past Opera would just crash and I had to restart Opera. At least now Opera doesn't crash. 

 What could be causing this? 
 Could it be some fluke somewhere in the www network?
 Or could it be some type of attack or possible virus/malware/spyware attack? 

 In the several years using Linux I have never gotten any virus/malware/spyware but this freeze, dimming, then resuming is something new and am curious as to what may be causing it.

---

### Post by critin on 2012-07-26
Does opera have a troubleshooting link under Help?  Have you checked add-ons for needed updates? You've probably already tried all this, but just in case...

---

### Post by cybrsaylr on 2012-07-26
Yes Opera has help Forums but I tried going here first.
I don't really bother with adding add-ons and pretty much use Opera as is.

---

### Post by cybrsaylr on 2012-07-27
Bump.

Anyone know what's causing this?

---

### Post by PaulW2U on 2012-07-27
> **cybrsaylr said:**
> 
Anyone know what's causing this?

I don't know what is causing your problems but I've just tried to download the latest development version of Opera using Opera itself. Each time I tried, Opera froze.

I'm now using Opera 12.01.1528, a Release Candidate for the next maintenance release. I actually used Firefox to download it but I can now download other versions of Opera using Opera and select a download directory, I couldn't before as the program completely froze.

May be an upgrade to Opera 12.01 will solve your problems? I think it will be released sometime next week.

---

### Post by Frogs Hair on 2012-07-27
Opera 12 on 12.04 has been fine so far . The 11.65 build on 11.10 gave me a few minor problems and running Opera Next solved that.

---

### Post by cybrsaylr on 2012-07-27
I usually just wait for the latest releases now as they come through Ubuntu Update Manager. This bug is more of an annoyance since Opera doesn't crash like it used to in the past. 

Posted this bug in the Opera Help Forums but got no response as yet. Opera Linux Forums are usually pretty dead, that's why I posted for help here. More action to be found here.

---

### Post by cybrsaylr on 2012-07-31
Bump!
Anyone got any solution?

---

### Post by sixnetonoffun on 2012-07-31
Have you tried shutting off the Appearance>>checkbox "Enable Special Effects"? 

Opera-Next
Version 12.50 
Build 1497

Only time I've noticed issues like that was when configuring firewall blocklists with PeerGuardian on the fly and was blocking the certificates on https sites. 

Aside from issues on some poorly scripted Java sites making use of Ajax like scripts. But then there was an obvious hang while downloading the elements.

Using Oracle-Sun Java(TM) Plug-in 1.7.0_05

---

### Post by cybrsaylr on 2012-08-01
sixnetonoffun,

Will give that a try.
Just disabled "Enable Special Effects"

---

### Post by black veils on 2012-08-01
this wouldnt necessarily be a solution, but if the special effects setting doesnt help, try choosing:

**preferences** >> **advanced** >> **content** >> **enable plug-ins only on demand**

---

### Post by vasa1 on 2012-08-01
> **black veils said:**
> this wouldnt necessarily be a solution, but if the special effects setting doesnt help, try choosing:

**preferences** >> **advanced** >> **content** >> **enable plug-ins only on demand**

That ^^^ and try turning off hardware acceleration (this GPU/GPL stuff).

I *occasionally* run Opera (Opera/9.80 (X11; Linux i686; U; en) Presto/2.10.289 Version/12.00) with Click to Play "on" and the fancy stuff off. No crashes, no freezes.

---

### Post by cybrsaylr on 2012-08-01
I disabled "Enable Special Effects" 19 hours ago as sixnetonoffun suggested and it has not once froze, dimmed down then resumed since. Am hoping that did the trick.

Also have noticed Opera is a bit snappier than before. Not sure if disabling "Enable Special Effects" had anything to do with that, or the recent 'Java updates' downloaded and installed today.

---

### Post by cybrsaylr on 2012-08-03
Well I may have spoken to soon.
In the last day this bug has happened but only twice. Once about 2 hrs after my last post and then once more a few hours ago. However this is an improvement because it used to happen several times a day before doing that tweak.

On the plus side Opera 12 is not crashing.

---

### Post by Frogs Hair on 2012-08-03
Have you install Opera Next ? Opera 12.01 stable came via the update manager yesterday and there were a number of fixes.

---

### Post by cybrsaylr on 2012-08-03
Frogs Hair, just did that upgrade to 12.01 minutes ago.
It didn't popup for me, had to go looking for it and then update to 12.01. Using 12.01 now. 
Will keep my fingers crossed and hope it was fixed.

---

### Post by cybrsaylr on 2012-08-26
Upgraded one of my laptops to Ubuntu 12.04 to see if that helped and it didn't. Still get those freeze/dim/then resumes but not as frequently using Opera 12.01.

---

