---
title: "Desktop effects could not be enabled"
date: 2009-03-19
forum: Desktop Environments
---

### Post by Etamami on 2009-03-19
I just launched Ubuntu, and suddenly it the effects were disabled, and I can't reactivate them, because it says:

"Desktop effects could not be enabled"

Is there a solution for this? ...can I force to enable the effect back? :confused:

Thanks for helping! :KS

*PS: It's all updated Ubuntu 8.10!*

---

### Post by nelskurian on 2009-03-19
> **Etamami said:**
> I just launched Ubuntu, and suddenly it the effects were disabled, and I can't reactivate them, because it says:

"Desktop effects could not be enabled"

Is there a solution for this? ...can I force to enable the effect back? :confused:

Thanks for helping! :KS

*PS: It's all updated Ubuntu 8.10!*

While in hardy i got the same error.But after a fresh install with ubuntu intrepid i got the one.cheers;;I think it may be due to the lack of proper drivers related to display enhancement.
if the system installed with alternate cd,compiz and appropriate drivers installs by deafault. 
   You need to install all the updated packages in synaptic.

---

### Post by Etamami on 2009-03-19
Well, it worked...and since I didn't change anything, it just says no. Btw...ofcourse every compiz stuff is installed, well, except Compiz-Fusion...I just added it now, and there I did some changes, but only I could re enable the windows effect, not the desktop once. :(

---

### Post by Etamami on 2009-03-28
Funny, now again nothing worx.

I try to enable on the desktop, it won't enable it and even in compiz set all animations and decoration are just simply not working anymore.

Any solution for this issue? :confused: *except of reinstalling Ubuntu! :(

---

### Post by MockY on 2009-03-31
I'm surprised that not more people have issues with this. 4 of my systems, all running various GeForce cards, suddenly disabled the Compiz and refused to enabled it again. All systems showed these symptoms simultaneously, so it has to do with one or more of recent updates.

None, ALL of these systems ran Visual Effects set on Extra perfectly ever since the Intrepid release (so almost 5 months now) and ALL of the systems refused to enable desktop effects at the same time. So the problem must be with some recent updates. I have 2 laptops that uses Intel graphics, and none of those systems got these issues after the recent updates, so it smells like it is related to Nvidia drivers.

I had to manually reinstall the Nvidia drivers found [here]("http://www.nvidia.com/object/linux_display_ia32_180.44.html") again in order for all systems to be able to enable it again.

I don't know which update that broke this (there has been no kernel updates in a while) but I hope someone could shed some light on this bizarre issue.

I guess with Jaunty around the corner, this is not to much of a pain in the rear end, but I really hope this "bug" dies with Intrepid.

---

### Post by Etamami on 2009-04-01
Wow, nice to know! Actually, you might be right with that update thing, because in my chase it also happened after some updates.

So you thing 9.04 won't have the bug? Let's hope so! ;)

Meanwhile I will try to install manually the driver from Nvidia! :KS Thanks for the hint!

---

### Post by Etamami on 2009-04-01
> **MockY said:**
> I had to manually reinstall the Nvidia drivers found [here]("http://www.nvidia.com/object/linux_display_ia32_180.44.html") again in order for all systems to be able to enable it again.

Can I ask how did you install this driver? Because I did it somehow, but I'm not quiet sure if i did it right, because the problem didn't go away.

1. Downloaded to Desktop, made it executable.
2. <CTRL> <ALT> F1
3. sudo /etc/init.d/gdm stop
4. sudo ./NVIDIA....file
5. it installed it self
6. sudo /etc/init.d/gdm start
7. setup settings

Is this the right way?

---

### Post by Clay_Banger on 2009-04-01
ok, so i had the same problem. after updating ~30 packages, no go on visual effects.
reinstalling the nvidia driver from the website worked though.

if you are using the nvidia driver from the repo, u may just b able to reinstall it, rather then manually install the one from nvidia's site.

would love to find out which update it was that did it though..

---

