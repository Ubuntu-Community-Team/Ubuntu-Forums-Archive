---
title: "Need a little help with my E1505n"
date: 2007-10-16
forum: Dell  Ubuntu Support
---

### Post by mike.123850 on 2007-10-16
I have the 256 Nvidia GeForce Go 7300 Turbo Cache video card.  I did the upgrade from 7.04 to 7.10 tonight. My resolution was fine until my monkey hands started messing around and changed things. Now my resolution will not stay  and I have to change it after every re-boot.  I do click on save the settings change, unfortunately, the settings are not saved.


If I go into System---Administration---Screens and Graphics it says:

Screen:
Model: Dell 1600 x 1200 laptop display
Resolution: 1440 x 900 at 53 Hz

Graphics Card:
nvidia

At bootup I do see the Nvidia graphic and I do have the it enabled in Restricted Drivers.

Is this all proper? Help .... pretty please?

Mike

---

### Post by troy1of2 on 2007-10-16
My E1505n says -

Model: Custom 1
Resolution: 1024 X 768 at 60Hz

Graphics Card - i810 - Intel Integrated Graphics Chipsets, in...

---

### Post by mike.123850 on 2007-10-16
Oops, sorry ....DUH! I should have put what video card I have. I have the 256 Nvidia GeForce Go 7300 Turbo Cache video card.

Sorry,
Mike

---

### Post by mike.123850 on 2007-10-16
Ok, I sorted it out. In a terminal window I ran sudo nvidia-settings, redected and saved to the X.org file. Everything seems to be working fine now.

Mike

---

### Post by troy1of2 on 2007-10-16
> **mike.123850 said:**
> Ok, I sorted it out. In a terminal window I ran sudo nvidia-settings, redected and saved to the X.org file. Everything seems to be working fine now.

Mike


I thought you probably did have based on what you said but just in case any of that info might have been useful I thought I might as well post it. Glad you got things working again!

---

### Post by mike.123850 on 2007-10-16
I appreciate you chiming in though. I tell ya, nothing like shooting myself in the foot sometimes.

Ok, now my System---Administration---Screens and Graphics correctly says:

Screen:
Model:Seiko
Resolution: 1440 x 900 at 50 Hz

Graphics Card:
nvidia

Thanks again,
Mike

---

### Post by cody50 on 2007-10-16
other than the video stuff you just fixed, how did the upgrade go for your 1505n? I have one as well but am tentative about upgrading for fear of breakage. Also, does anyone know how an upgrade would affect the warranty?

---

### Post by mike.123850 on 2007-10-16
Obviously your mileage mayl vary, but here is what I did.

First I backed up stuff I wanted to keep. Second, I downloaded and burned two Ubuntu CD's. One was the Dell remastered Ubuntu 7.04 for the E1505n, which can be found here:
[http://linux.softpedia.com/progDownload/Dell-Remastered-Ubuntu-Download-30344.html](http://linux.softpedia.com/progDownload/Dell-Remastered-Ubuntu-Download-30344.html)

The second cd was the alternate Ubuntu 7.10rc cd. Alternate is used for upgrading your current 7.04. Mirrors found here at the bottom of the page:
[http://www.ubuntu.com/testing/710rc](http://www.ubuntu.com/testing/710rc)

Once I had both of these, burned and ready to go I proceeded with the upgrade  using the update manager. The cd's for if things went horribly wrong. :)

I used these commands:
Alt-F2
update-manager<space> -d

Which brought up the Update Manager, which in turn told me there was a new version .... Ubuntu 7.10. I went for the update and let her run.

So far, things seem to be doing fine. I haven't tested everything yet, but right now it all looks good. 

Mike

---

### Post by cody50 on 2007-10-16
ok, cool thanks for the info. be sure to post anything else important that you find. I want to try to wait a little while before upgrading to make sure there are no kinks, but it will be very hard to resist!

---

### Post by mike.123850 on 2007-10-16
I'll let you know if anything odd pops up. So far today, there have been no updates so it's probably getting pretty close to being finalized. Well, as finalized as it'll get until they put out more updates after the final release. LOL!

What I tell folks is this. If your system is working and doing what you need .... leave it alone until the final release is available. Then wait a little more for the subsequent updates to show up. Then make the decision if the new version will be "better" for your needs or not. I always caution people against jumping on the upgrade train because there are always risks involved.

My laptop is just a convenience item and nothing important is on it. If I have to install from scratch it's no big deal. Most people aren't in this same category.


Nothing wrong with waiting. :)

Mike

---

