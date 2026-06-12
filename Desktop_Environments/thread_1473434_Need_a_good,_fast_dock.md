---
title: "Need a good, fast dock"
date: 2010-05-05
forum: Desktop Environments
---

### Post by MisterLambda on 2010-05-05
I'll need a somewhat Macish dock that can run well on 256 MB RAM, and can launch and switch applications, of course.

---

### Post by fabounet on 2010-05-05
I can recommend GLX-Dock, but you could also search on the net, I guess it would take you 5 minutes.
[http://www.glx-dock.org/ww_page.php?p=From%20the%20repository&lang=en]("http://www.glx-dock.org/ww_page.php?p=From%20the%20repository&lang=en")

(256M ... do you have compositing ?)

---

### Post by KdotJ on 2010-05-05
Avant window navigator (AWN) is nice. Is it available for xubuntu?

---

### Post by vaiocomputer on 2010-05-05
I recommend Docky or Cairo dock or Avant Window Manager, which should all be in the launchpad repos if you want the latest versions, but should also be in the Ubuntu ones too.  

I use Avant.

---

### Post by MisterLambda on 2010-05-05
No composition - and I'm pretty sure things that run in Ubuntu will run in Xubuntu, same base.

I've got xfapplet installed, so I can use GNOME panel applets in XFCE.

---

### Post by xxeper on 2010-05-05
I'd been a Docky/GnomeDo guy for some time now. Tried the others in 8.x and 9.x and never really liked them. They all seemed to intrusive, buggy, etc or just plain didn't work like a 'real' dock.

I installed Cairo-Dock on 10.04 today and I don't think I can ever go back to Docky.

Just takes a little time to configure it the way I like it, but man is it good. Stable too, and that's key for me. I can't sit here and relaunch the dock over and over again simply because it has ADD and wandered off. It's been rock-solid so far, and it looks fantastic. Highly tweakable, too.

---

### Post by Jose Catre-Vandis on 2010-05-05
It's not a dock in the way you mean it, but **wbar** does a great job for me. make sure you track down **wbarconf** to help set it up.

Another similar one is **adeskbar**

---

### Post by MisterLambda on 2010-05-07
I can't use compositing, nor the fancy-schmancy memory eating docks - which removes a crapton. wbar can't switch applications, and adeskbar appears to be in it's infancy.

---

### Post by fabounet on 2010-05-07
Cairo-Dock doesn't need composite (it has a fake transparency mode).

---

### Post by KdotJ on 2010-05-07
I'm a fan of Cairo-dock too, although I don't really like how
it has so much stuff goin on when you install it. Like the flames etc. And it can be a little confusing to customize and change the specific tweaks. But overall a really nice slick dock

---

### Post by Coburn on 2011-01-10
> **MisterLambda said:**
> I'll need a somewhat Macish dock that can run well on 256 MB RAM, and can launch and switch applications, of course.
The XFCE Panel has that capability.
* Create a new panel from Applications Menu | Panel
* Configure width and orientation
* Configure transparency or Autohide
* Check "fixed position" to allow further options
* _Manually configure launchers_.  Most apps live in /usr/bin/
* Manually configure launcher icon.  Choose "Application Icons" from the dropdown list, or go to "All Icons" if you can't find one for your installed program.  There is also an option to use "Bitmaps" if, like me, you want to run something like Amaya from a userspace directory, where its icon also lives.
* Add panel applets to enable icons for running applications, Trash, Clock, etc.
The advantage of this dock is that it does not require you to install a memory-hungry third-party dock like Docky, AWN, or Cairo-Dock.

---

### Post by Coburn on 2011-01-10
> **MisterLambda said:**
> I'll need a somewhat Macish dock that can run well on 256 MB RAM, and can launch and switch applications, of course.
The XFCE Panel has that capability.
* Create a new panel from Applications Menu | Panel
* Configure width and orientation
* Configure transparency or Autohide
* Check "fixed position" to allow further options
* _Manually configure launchers_.  Most apps live in /usr/bin/
* Manually find the icon you want by clicking on the default icon.  Choose "Application Icons" or "All Icons" from the dropdown list, or if you have something with its own icon elsewhere, like Aptana Studio, choose "Bitmap"
* Add panel applets to enable icons for running applications, Trash, Clock, etc.
The advantage of this dock is that it does not require you to install a memory-hungry third-party dock like Docky, AWN, or Cairo-Dock.

I use Docky on my x64 computer running Ubuntu 10.10, but on my little old Thinkpad with Debian Squeeze, I actually find that the XFCE Panel gives me more feature options than Docky!

---

### Post by azertyh on 2011-01-11
> **Coburn said:**
> The XFCE Panel has that capability.
* Create a new panel from Applications Menu | Panel
* Configure width and orientation
* Configure transparency or Autohide
* Check "fixed position" to allow further options
* _Manually configure launchers_. Most apps live in /usr/bin/
* Manually configure launcher icon. Choose "Application Icons" from the dropdown list, or go to "All Icons" if you can't find one for your installed program. There is also an option to use "Bitmaps" if, like me, you want to run something like Amaya from a userspace directory, where its icon also lives.
* Add panel applets to enable icons for running applications, Trash, Clock, etc.
The advantage of this dock is that it does not require you to install a memory-hungry third-party dock like Docky, AWN, or Cairo-Dock.
 
 
 +1
it's what i have now.

---

