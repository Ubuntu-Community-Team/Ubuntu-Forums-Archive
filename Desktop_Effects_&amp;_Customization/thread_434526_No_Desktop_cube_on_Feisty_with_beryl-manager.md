---
title: "No Desktop cube on Feisty with beryl-manager"
date: 2007-05-06
forum: Desktop Effects &amp; Customization
---

### Post by ravinsp on 2007-05-06
Hi all,

I have Ubuntu 7.04 on my laptop. It's video card is ATI X200M.

I installed xserver-xgl and beryl (from beryl repository) according to [**_[COLOR="Blue"]this thread[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=399643&highlight=x200m+beryl") and they work fine. But the only problem is desktop cube doesn't get activated. I tried changing settings in beryl settings manager but it didn't work. How can I fix this?

I've also read another thread on same problem but it reffers to compiz manager which comes with ubuntu.

Thanks
-RavinSP-

---

### Post by ethos101 on 2007-05-06
According to [http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon"):
> 2D Acceleration Only

    * Xpress 200M Northbridge integrated GPUs


I was just about to do the same on my laptop and found this.  I guess that means no cube.  Am I wrong?  I hope so.  Anybody feel free to correct me please.

---

### Post by ravinsp on 2007-05-06
Hi,

I don't beleive that because **desktop cube works under compiz manager**(which comes with Feisty). When I switch to beryl manager, then no cube.

(or compiz is drawing the cube on 2D surface while beryl is drawing it in 3D. I dont know!)

Anyway don't give up yet!

-RavinSP-

---

### Post by nevin on 2007-05-07
i'm having the exact same problem, but the thing is, the 3D desktop did work, atleast before i rebooted after everything with beryl was set up...

i have a x300m, and the 3d desktop worked when i had edgy installed, perfectly infact.

i dont know what's wrong, but i know it can work.... it just doesnt.

haha, well, hopefully someone with more computer knowledge than me will come up with a fix, or show us what's wrong.

---

### Post by ravinsp on 2007-05-08
Found a solution to the cube problem here:

[http://forum.beryl-project.org/viewtopic.php?f=37&t=5094&st=0&sk=t&sd=a&start=10]("http://forum.beryl-project.org/viewtopic.php?f=37&t=5094&st=0&sk=t&sd=a&start=10")

You just have to delete the file **[COLOR="DarkRed"]/home/<user>/.beryl/settings[/COLOR]** and just logout and login. Then the cube works!

Good luck!

---

