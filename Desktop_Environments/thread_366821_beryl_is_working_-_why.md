---
title: "beryl is working - why?"
date: 2007-02-21
forum: Desktop Environments
---

### Post by martinmartinmartin on 2007-02-21
Hi there

This is my very first post on ubuntuforums so please bear with me..

I've made a clean edgy install, installed nvidia driver from albertomilone.com, enabled AIGLX and installed  latest beryl. And the thing is: it works - great!  But when I start beryl manager it states that GLX_EXT_texture_from_pixmap has failed (see below), I thought this option was mandatory for beryl to work??? Im puzzled, can enyone shed some light? 


**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : failed

No GLX_EXT_texture_from_pixmap
beryl: No GLXFBConfig for default depth, falling back on visinfo.
Reloading options

---

### Post by john.nicholls on 2007-02-21
> beryl: No GLXFBConfig for default depth, falling back on visinfo

I have seen references in the forums to Beryl requiring a specific depth; you could search the forums to try and find something about this? In your case, if falling back on visinfo works, I wouldn't worry to much about it; just getting Beryl to work is something of an achievement.

---

### Post by martinmartinmartin on 2007-02-22
Thanks for your reply, you're right maybe I should just enjoy the eyecandy and forget about this. The thing is I'm newbee'ish in the linux world and I'm eager to learn more, hence I ask questions when something like this happens :-)

regards

---

### Post by pure fusion on 2007-03-09
Hey,
I have the same problem and for right now my Beryl works too, but... previous to this time beryl had done this before except after rebooting, it would give the error but not still run after the initial run. I havent tried rebooting my computer yet this time around because Im afraid Ill loose the pretty wobbley windows. Any help would be apreciated seeing as that Im new to Linux too.

---

