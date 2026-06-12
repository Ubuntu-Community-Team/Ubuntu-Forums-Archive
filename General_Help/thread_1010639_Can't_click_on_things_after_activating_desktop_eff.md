---
title: "Can't click on things after activating desktop effects"
date: 2008-12-14
forum: General Help
---

### Post by infinitejones on 2008-12-14
First of all, here's my setup:

HP Pavilion dv6000 with nVidia GEForce 8400M GS. Fresh install of Intrepid with Gnome (well, almost fresh - I'll get to that in a minute), all fully updated. nVidia driver 177 installed via Hardware Drivers. Compiz installed via Synaptic, with all the dependencies left as they are.

The only thing that isn't "fresh" about the installation is the fact that I have my home folder in a separate partition, which I didn't format when I re-installed Intrepid.

Now, here's the problem - when I activate Visual Effects from the Appearance menu (either 'normal' or 'extra'), mouse clicks don't work. The pointer turns into the little hand that moves windows around, but it doesn't click the button it's hovering over. I can click the button by selecting it using tab and hitting enter, but not by pointing to it and clicking. This is the case everywhere on the screen.

When I select 'restore previous settings', it goes back to no desktop effects and it's all fine.

It started happening after I'd tried installing compiz via git using a script I found linked to on Ubuntu Forums. Just to have a look at some new desktop effects. "A-ha!" I hear you cry. "That's your problem!" But no - even after re-formatting my / partition and a fresh install, the problem's still there.

Which leads me to think that it's some kind of setting in a hidden folder in my home drive. Either that, or something to do with gconf, which I don't really understand. I went through all the hidden folders deleting everything that looked like it was anything to do with compiz, compizconfig, or emerald (which I had installed previously, and it worked fine) but even after doing that (plus aptitude remove --purge compiz) and re-installing, the same thing still happens.

Any ideas? I guess it's not a major issue if I don't activate desktop effects, but it's always worked fine for me in the past, and Ubuntu just doesn't feel "right" on my laptop if I don't have some wobbly windows and spinning cubes...

---

### Post by eternalnewbee on 2008-12-14
Hi infinitejones.
I don't have a solution for you (unfotunately), but after reading your post, I think your problem is with the driver.
Here are two links that might be useful to you:
[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)
[http://ubuntuforums.org/showthread.php?t=1002828](http://ubuntuforums.org/showthread.php?t=1002828)

---

### Post by infinitejones on 2008-12-14
> **eternalnewbee said:**
> I think your problem is with the driver.


Hmmm... thanks, but I'm not sure the problem's with the driver - desktop effects had been working perfectly well with nVidia 177 prior to this problem appearing. The driver hadn't changed but the problem still appeared, which suggests the problem isn't the driver!

Anyway... I tried installing 180.11 using the Jaunty repository (as per the second link) but I just got a dialogue box saying "Desktop effects could not be enabled" when I tried to enable them.

Also, Ubuntu wanted me to do a partial upgrade using that Jaunty repository and I'm not so keen on that (yet). I removed that repository and downgraded the nVidia driver back to 177, wondering if maybe that would solve the problem... and it hasn't. In fact, I'm still getting the the "desktop effects could not be enabled" dialogue box.

Remember, this problem has persisted following a complete re-installation of Intrepid, where the root partition was re-formatted. The home partition wasn't re-formatted, and the problem's still there - therefore surely the problem is somewhere in my home partition! 

Maybe I should back up and reformat my home partition...

Any other suggestions before I try that?

---

### Post by eternalnewbee on 2008-12-14
I'm stuck there with you, too. Sorry mate.
But I'm keeping an eye on this thread:wink:

---

