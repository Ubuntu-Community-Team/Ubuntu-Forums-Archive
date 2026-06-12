---
title: "tweaking Compiz for speed (or whatever)"
date: 2007-04-16
forum: Desktop Effects &amp; Customization
---

### Post by dr_d12 on 2007-04-16
I am interested in your tips to tweak Compiz with gconf-ed (for speed or whatever). 
Here are two settings that I changed to speed up cube rotation and minimize in Compiz0.5. Your mileage may vary.
Cheers.


Run: gconf-editor

Navigate to:
/apps/compiz/plugins/minimize/screen0/options/speed
right-click 'speed' and select 'edit'
increase the minimize speed from 1.5 to 3.5 (test different speeds on the Configuration Editor window!)

increase cube rotation speed from 2.0 to 3.0:
/apps/compiz/plugins/rotate/screen0/options/speed

Increase expose speed from 1.5 to 3.5:
/apps/compiz/plugins/scale/screen0/options/speed

---

### Post by JAPrufrock on 2007-04-17
Why don't you use compiz settings manager?

---

### Post by dr_d12 on 2007-04-17
Compiz 0.5 doesn't have one yet, or at least I wasn't able to find one to install at the time. Gconf-ed isn't so bad once you have a look around inside.
The link I have (from [http://forum.compiz.org/viewtopic.php?t=153&highlight=settings+manager](http://forum.compiz.org/viewtopic.php?t=153&highlight=settings+manager)) for compiz-settings manager deb for feisty is:
[http://compiz.biz/compiz-settings/compiz-settings_0.07-2_i386.deb](http://compiz.biz/compiz-settings/compiz-settings_0.07-2_i386.deb)
but the link is dead. I don't think it's ready yet.
-Dave

---

