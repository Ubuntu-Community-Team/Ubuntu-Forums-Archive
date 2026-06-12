---
title: "Compiz-Fusion fresh install  -- Update help needed!"
date: 2007-07-31
forum: Desktop Effects &amp; Customization
---

### Post by fofo412 on 2007-07-31
Hey!

Thanks to all of the great How-To's on this forum, I have successfully installed compiz-fusion on my laptop with XGL (even with my crappy ATI Radeon Xpress 200m). . .

My problem is that Ubuntu is prompting me to install updates for compiz-everything, and I have this feeling that if I install these, my entire install will break to pieces.

Is there a way to tell Ubuntu to NOT prompt me with these selected updates?  I do like being notified of other updates though.

Help, or a redirect will be greatly appreciated!


Thanks.

-Chris

---

### Post by psyopper on 2007-07-31
The easy way is to open Software Sources and ucheck the box next to the repositories that you added to install compiz-fusion.

System | Administration | Software Sources | Third-Party Software.

I wish I would have done this back in the beginning of July, Compiz is only getting slower as time goes on...

---

### Post by bl4k3r on 2007-08-01
> **fofo412 said:**
> 
Thanks to all of the great How-To's on this forum, I have successfully installed compiz-fusion on my laptop with XGL (even with my crappy ATI Radeon Xpress 200m). . .

I tried to get Compiz Fusion up and running on my HP notebook which has the same graphics card. Unfortunatley, compiz --replace throws an error! I suppose that this is an issue with either the graphics driver or the XGL session setup.

I would appreciate if you could give me some tips on your XGL and drivers setup! Thanks! :)

---

### Post by fofo412 on 2007-08-01
> **psyopper said:**
> The easy way is to open Software Sources and ucheck the box next to the repositories that you added to install compiz-fusion.

System | Administration | Software Sources | Third-Party Software.

I wish I would have done this back in the beginning of July, Compiz is only getting slower as time goes on...


Thank you!  This worked great, and quick response too!

---

### Post by fofo412 on 2007-08-01
> **bl4k3r said:**
> I tried to get Compiz Fusion up and running on my HP notebook which has the same graphics card. Unfortunatley, compiz --replace throws an error! I suppose that this is an issue with either the graphics driver or the XGL session setup.

I would appreciate if you could give me some tips on your XGL and drivers setup! Thanks! :)

 Wow, thanks for the interest, and really hope I can help.

I used several different tutorials, and broke my install a few times before getting everything to settle properly.

My laptop is an amd64, with a FRESH Feisty (plain Ubuntu) install. . . 

1.) The first thing I did was apply the restricted ATI driver, and restart.

2.) I used the clean-up & prepare parts of this tutorial:

[http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)

(Installing the latest ATI driver via Envy broke my install, I had to [ctrl + alt + backspace] to log out of my XGL session and reinstall the old driver)

3.) I created an XGL session from this tutorial:

[http://ubuntuforums.org/showthread.php?t=399643](http://ubuntuforums.org/showthread.php?t=399643)

4.) After logging into the XGL, I followed the second part of this tutorial:

[http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)

5.) I installed emerald, and added the (Alt +F2) commands, separately, to the startup.


This is essentially what I did, but some may be slightly out of order, due to breaking things along the way, and going back to fix it.  After messing with things for ~25 mins, there really is not a lot to this install.  Post back with your progress.

---

### Post by bl4k3r on 2007-08-02
> **fofo412 said:**
> Post back with your progress.

Thanks, as I supposed, my XGL session was messed up. I did it your way, and everything works like a charm!

By the way, I have not got emerald installed (in contrast to your cited How-to), so if it's something berylish that your Ubuntu wants to update, you might want to try to remove emerald and beryl packages. My system is completely beryl-free! ;)

---

### Post by fofo412 on 2007-08-03
> **bl4k3r said:**
> Thanks, as I supposed, my XGL session was messed up. I did it your way, and everything works like a charm!

By the way, I have not got emerald installed (in contrast to your cited How-to), so if it's something berylish that your Ubuntu wants to update, you might want to try to remove emerald and beryl packages. My system is completely beryl-free! ;)

I unselected the thrid party software updates that I had installed separately, and everything is working.

I'm glad that this "procedure" worked out!

My next step is to find the plugins I do not have, and acquiring what I need (package-wise, knowledge included) to compile apps / things from source. . .

---

### Post by bl4k3r on 2007-08-03
> **fofo412 said:**
> My next step is to find the plugins I do not have, and acquiring what I need (package-wise, knowledge included) to compile apps / things from source. . .

What plug-ins do you mean? I got quite a lot with my compiz install! Maybe that's what your Ubuntu wants to upgrade? I got the latest compiz build, i.e. no update notifications, by the way, so I guess you could do that upgrade without messing up your system, too.

---

### Post by fofo412 on 2007-08-03
Maybe I should try that upgrade. . .

 Worst case, my install breaks, and I have to take 30 mins to remove / replace Compiz-Fusion again.  That really isn't a big deal.

I don't know what specific plugins I am missing, but I do not have everything that is in "The" You Tube demo video (mainly the window switching).  Hopefully I can play with it a little more tonight.

---

