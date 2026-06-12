---
title: "No Gnome 3 after upgrade to 11.10"
date: 2011-11-27
forum: Desktop Environments
---

### Post by trustme on 2011-11-27
In 11.04 I installed gnome 3 and it was about to work.
After upgrading to 11.10 gnome 3 stoped to work.
In my X selection screen I see gnome, gnome clasic and gnome clasic (wo effects).  
When I select gnome, I will only get gnome 2.x, same in both other.  

gnome-shell --version 
GNOME Shell 3.2.1  

lspci | grep -i nvidia 
01:00.0 VGA compatible controller: nVidia Corporation GF106 [GeForce GT 555M] (rev a1)  

/usr/lib/nux/unity_support_test -p 
Xlib:  extension "GLX" missing on display ":0.0". 
Xlib:  extension "GLX" missing on display ":0.0". 
Xlib:  extension "GLX" missing on display ":0.0". 
Error: unable to create the OpenGL context   

Could you please help me out of this issue.  
BR

---

### Post by bhupinderjitbawa on 2011-11-27
buddy i got the same problem have nvidia geforce.
they are not working anymore and getting same error

---

### Post by jimmydean886-2 on 2011-11-27
GNOME shell has changed a lot since Natty. The PPA version, for one, has a tenancy to mess up the system. Try installing the GNOME-shell package from the official repos.  You may or may not have extension capability, but everything else will be there.

---

### Post by Copper Bezel on 2011-11-27
That's not necessarily true. This looks more like a graphics driver problem.

You *should* purge the Gnome 3 PPA using ppa-purge, though, and start from there. 11.10 uses Gnome 3 to begin with, without any need for a PPA.

---

### Post by trustme on 2011-11-27
In the meanwhile I killed my Ubuntu, so the logical consequence was to install a fresh 11.10.
Done.

Now the only thing I did was to install gnome 3.

Same issue than before ... all three commands with the same output.

---

### Post by bluexrider on 2011-11-27
> **Copper Bezel said:**
> That's not necessarily true. This looks more like a graphics driver problem.

You *should* purge the Gnome 3 PPA using ppa-purge, though, and start from there. 11.10 uses Gnome 3 to begin with, without any need for a PPA.

I agree. You may want to run in fallback and check your drivers for compatibility

---

