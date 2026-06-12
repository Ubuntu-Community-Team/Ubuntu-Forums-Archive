---
title: "Dell Inspiron 8600 upgrade question"
date: 2007-07-21
forum: Desktop Effects &amp; Customization
---

### Post by stupots on 2007-07-21
Hi all,

First post, so please be gentle ;)

I'm currently running Edgy on a Dell Inspiron 8600 which has an ATI Mobility Radeon 9600 card.  Just to clarify, there are two versions of this laptop, which either have a 1280 x 800 or 1900 x something-or-other display.  I've installed Beryl and it works like a charm, using the open-source ATI driver (which was installed automatically)

When running Feisty, there are well-documented problems with screen flicker when using the open-source ATI driver on 1280 x 800 screens, but no documented solution.  The higher res versions don't appear to have this problem.

If I upgrade my installation from Edgy to Feisty, is there a way I can use the Edgy version of the open-source ATI driver?  And if so, how do I do it?  I assume I have to use the open-source driver because the official ATI driver does not support composite features.  Or am I wrong on this?

Any help appreciated,
Stuart

---

### Post by overdrank on 2007-07-22
> **stupots said:**
> Hi all,

First post, so please be gentle ;)

I'm currently running Edgy on a Dell Inspiron 8600 which has an ATI Mobility Radeon 9600 card.  Just to clarify, there are two versions of this laptop, which either have a 1280 x 800 or 1900 x something-or-other display.  I've installed Beryl and it works like a charm, using the open-source ATI driver (which was installed automatically)

When running Feisty, there are well-documented problems with screen flicker when using the open-source ATI driver on 1280 x 800 screens, but no documented solution.  The higher res versions don't appear to have this problem.

If I upgrade my installation from Edgy to Feisty, is there a way I can use the Edgy version of the open-source ATI driver?  And if so, how do I do it?  I assume I have to use the open-source driver because the official ATI driver does not support composite features.  Or am I wrong on this?

Any help appreciated,
Stuart

Hi and welcome, if you would search for that card on the forums you would see a lot of threads where some work and some have trouble getting it to work. So I would say that if you have a working system and you like it without major issue then stick with it. 
I would still be with dapper if the support for bery was not stopped, I do you feisty now for the wireless support on my laptop but on the desktop I run edgy with beryl and dapper for rock solid support. So if you choose to upgrade just research and be prepared and all the best. Good Luck and welcome again. :KS

---

### Post by stupots on 2007-07-23
A follow up:

Well, I took the plunge and upgraded to Feisty.  As expected, it used the open-source ATI driver which resulted in screen flicker.

I tried following the instructions in the following thread to get Compiz/Beryl working using the fglrx driver:

[http://ubuntuforums.org/showthread.php?t=493074]("http://ubuntuforums.org/showthread.php?t=493074")

The only step which wasn't explained was to chmod the startxgl.sh file to 777.

I now have fglrx with xgl, and have even got video windows rendering properly even when rotating the cube, and as thumbnails etc.

I can definitely recommend the above thread to anyone else with Inspiron 8600 problems.

Regards,
Stuart

---

### Post by scottylans on 2007-07-28
Stuart, your response is really appreciated, I might try this tommorow.
I also have the 8600, with 1280x800 screen and 9600 mobile, I loved the 3D effects but the flicker sucked! :(

---

### Post by scottylans on 2007-07-31
WARNING TO ANYONE READING THIS THREAD WITH AN 8600.

Do not follow the instructions in the link provided, there's clearly something else which has to be done first, I followed the instructions and it screwed up my Ubuntu install, network manager disapeared and I still had Dell 8600 glitches.

Avoid.

EDIT:
Thread here with info on my issues.


[http://ubuntuforums.org/showthread.php?p=3109513#post3109513](http://ubuntuforums.org/showthread.php?p=3109513#post3109513)

---

### Post by scottylans on 2007-08-08
This problem persists in gusty beta as well! - surprising.

[http://ubuntuforums.org/showthread.php?t=520518](http://ubuntuforums.org/showthread.php?t=520518)

---

