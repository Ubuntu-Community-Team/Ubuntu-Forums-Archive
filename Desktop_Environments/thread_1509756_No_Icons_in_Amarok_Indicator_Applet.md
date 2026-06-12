---
title: "No Icons in Amarok Indicator Applet"
date: 2010-06-14
forum: Desktop Environments
---

### Post by gnomeout on 2010-06-14
I have this issue where there are no icons in the indicator applet menu for Amarok. The picture kind of says it all... 

I have seen similar posts for this problem but nothing I have tried works, and the posts with my EXACT problem have no solution...

I have heard that sometimes this issue is fixed in new user accounts that are created. However the threads that mention this are usually talking about someone who has upgraded from an older Ubuntu. I have not upgraded.

I am using a clean installation of 10.04 Lucid Lynx, no upgrade and not even a backed-up/restored configuration file to be found. 100% fresh Ubuntu. So creating a new account should make no difference.

So why is this happening and how can I fix it?

SEE PICTURE FOR ISSUE

---

### Post by gnomeout on 2010-06-18
Bump... come on people, there has to be something I can do..

---

### Post by gnomeout on 2010-06-25
booooooo come on people, i still cant find anything to fix this crazy stupid error. Why is KDE so inexplicably incompatible with GDM?

FML

---

### Post by Little Bones on 2010-06-25
Do you have KDE installed on your computer?

---

### Post by gnomeout on 2010-06-25
Hey, thanks for replying, Little Bones. 

Yes, I do have KDE installed, the full thing, even the desktop manager(which should not be necessary). I also have the KDE-icons themes installed(I think the one I have set is "crystal"). And I checked the configuration file for KDE (the one hidden in the home folder somewhere, can't remember where but people with similar issues refer to it) and all the values in this file correspond to the correct icon themes that I definitely have installed for KDE.

So you see there is no technical reason I can find why this shouldn't be working... its got me stumped.

Thanks for any help.

---

### Post by gnomeout on 2010-06-30
F this sh*t... looks like I'm gonna have to resort to launchpad...

---

### Post by ITC on 2010-09-06
Look at post 18 and 19 @ [https://bugs.launchpad.net/ubuntu/+source/indicator-application/+bug/600302]("https://bugs.launchpad.net/ubuntu/+source/indicator-application/+bug/600302")

---

### Post by Shpadoinkle on 2010-09-06
I had he exact same problem when I used Amarok, but no solution. I would like to recommend Clementine, a port of Amarok.

[http://code.google.com/p/clementine-player/]("http://code.google.com/p/clementine-player/")

---

### Post by gnomeout on 2010-09-06
> **ITC said:**
> Look at post 18 and 19 @ [https://bugs.launchpad.net/ubuntu/+source/indicator-application/+bug/600302]("https://bugs.launchpad.net/ubuntu/+source/indicator-application/+bug/600302")

Haha, ya, I actually created that bug report and commented on the solution myself. (gnomeout=gnomed my 2 most common usernames)

I was very pleased, it is super easy and works perfectly!


If you want some good entertainment, you can read me being an ******* at the beginning of that bug report because a bunch of people thought it was a duplicate of a different bug. I am glad I held my ground or perhaps we would not be looking at this solution today.

---

### Post by ITC on 2010-09-06
Hehe, i was wondering if the users was the same person.
Now all we (or at least i) has to get fixed is so the "stop" button works in indicator applet.

---

