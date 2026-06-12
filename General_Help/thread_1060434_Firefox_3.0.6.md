---
title: "Firefox 3.0.6?"
date: 2009-02-04
forum: General Help
---

### Post by NoBugs! on 2009-02-04
Why won't my Firefox update to Firefox 3.0.6?
It's still 3.0.5.

---

### Post by avtolle on 2009-02-04
> **NoBugs! said:**
> Why won't my Firefox update to Firefox 3.0.6?
It's still 3.0.5.
Perhaps the new version isn't in the repos yet?

---

### Post by fragos on 2009-02-04
The Ubuntu team always verifies new releases before placing them in the repositories. There are a number of details that need to be checked before an Ubuntu DEB package is built. For example will the new release work correctly with versions of libraries included in the Ubuntu distribution.

---

### Post by exploder on 2009-02-04
The new version will most likely appear in the repos in a couple of days.

---

### Post by NoBugs! on 2009-02-05
Yes, but isn't it a bit serious to wait several days for a high-risk security update like this?
The update is only a security update, it shouldn't have dependency on any new libraries.

Here's what I'm noticing:
Time between Firefox security vulnerability made known to system updating:
On Windows: 0 days + number of days for system to notice the update.
On Ubuntu: 3+ days + number of days for system to notice the update.

---

### Post by sports fan Matt on 2009-02-05
I'd take a three day wait versus anything that windows does..at least with ubuntu and linux, you dont need to run all the bloated software that windows users do, that slows down your system.

---

### Post by philinux on 2009-02-05
> **NoBugs! said:**
> Yes, but isn't it a bit serious to wait several days for a high-risk security update like this?
The update is only a security update, it shouldn't have dependency on any new libraries.

Here's what I'm noticing:
Time between Firefox security vulnerability made known to system updating:
On Windows: 0 days + number of days for system to notice the update.
On Ubuntu: 3+ days + number of days for system to notice the update.

You can have it now. Just use ubuntuzilla.
[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

---

### Post by NoBugs! on 2009-02-09
This security update was released on the 3rd, that's almost a week ago. Do I really need to replace ubuntu-firefox with ubuntuzilla just to get a security update?

---

### Post by dalesd on 2009-02-28
I still haven't gotten this update.  
Build identifier: Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.5) Gecko/2008121623 Ubuntu/8.10 (intrepid) Firefox/3.0.5

What can I do?

---

### Post by steveneddy on 2009-02-28
System --> Administration --> Update Manager

Try manually updating first.

Also try opening up Synaptic 

System --> Administration --> Synaptic Package Manager

and see of there is a newer version available.

---

### Post by dalesd on 2009-02-28
Thanks, steveneddy.  I checked those two places and neither showed any update available.

---

### Post by steveneddy on 2009-03-02
Open up Synaptic

find Firefox and select it

at the top select Package

then force version and see if the newer version is ready for you.

If so, just upgrade and you are good to go.

---

### Post by dalesd on 2009-03-02
Thanks, but no luck with that either.

When I select Firefox, then Package -> Force Version... I just have 3.0.3+ and 3.0.5+ available.

---

### Post by Slim Odds on 2009-03-02
In Synaptic, under "Settings -> Repositories", go to the Updates tab and select "backports". Then see what you get.

My hardy shows 3.0.6 as the current version.

---

### Post by dalesd on 2009-03-02
Ok, I got it!

It was a problem with one of my settings in Synaptic.

Under Settngs -> Repositories, the Ubuntu Software tab, "Download From" had been set to some local server (whatever the 'best' server was).  I changed it to "Server for the United States", reloaded, and the update showed up.

Thanks all for your help.

---

### Post by emarkay on 2009-03-02
Waitaminute...

I just click on "Help/Check for Updates" in Firefox and if there is one, the update arrives "automagically" that way.

Surely this is also an acceptable method?

---

### Post by dalesd on 2009-03-02
> **emarkay said:**
> Waitaminute...

I just click on "Help/Check for Updates" in Firefox and if there is one, the update arrives "automagically" that way.

Surely this is also an acceptable method?

That's grayed out if you use the Firefox and updates from Canonical.

---

### Post by emarkay on 2009-03-02
> **dalesd said:**
> That's grayed out if you use the Firefox and updates from Canonical.

Interesting...  I just thought that that meant no were available...  Never noticed that - I had been running 3.1 betas till my system crashed (unrelated)

---

### Post by Slim Odds on 2009-03-02
> **dalesd said:**
> That's grayed out if you use the Firefox and updates from Canonical.

As they should be......

---

### Post by nanotube on 2009-03-05
Firefox 3.0.7 is out. grab it while it's hot. :)

it'll probably hit the repos in a week or two, too...

---

### Post by varanasi on 2009-03-05
3.0.7 is out.  I installed it.  And, many sites break it!  I have never had an Ubuntu upgrade result in such a significant problem before.

---

### Post by fragos on 2009-03-05
Was it an update from the main Ubuntu repository or did you jump the gun and get from another source? Ubuntu normaly delays availability of Firefox release until they've had time to test and packaage them.

---

### Post by varanasi on 2009-03-06
It's from the repository.  I wasn't particularly anxious to install the latest firefox, but I generally install whatever ubuntu wants me to.

Here's the output when I run firefox from a term window:
> 
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Segmentation fault

It doesn't break on every site.  NYTimes works fine.  Calculated Risk breaks it. 

How does one downgrade a program?  On the other hand, I wonder if it wasn't just firefox in the last upgrade.  Darn.

---

### Post by dalesd on 2009-03-06
Thanks for the update.  I got mine on both Ubuntu machines this morning.

varanasi, I had, I think, the same problem you're having until I restarted Firefox.  Have you tried turning it off and on again?  ;)

---

### Post by varanasi on 2009-03-06
Yes.  I restarted, disabled add-ons, uninstalled and re-installed.  Still broken.  The fact that it doesn't break on all sites makes me suspect it's some plugin or other that isn't compatible, but I'm stuck.

---

### Post by sports fan Matt on 2009-03-06
It was through update manager in my case.  In my case I havent tried every site but its definately a borked version

---

### Post by sports fan Matt on 2009-03-06
You cant post a url in the address bar at least here it wont show up.

---

### Post by sports fan Matt on 2009-03-06
ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],hidden)
5:()
6:()
7:currentEngine()
8:get_currentEngine()
9:updateDisplay()
10:init()
11:([object XULElement],7)
even when restarting

---

