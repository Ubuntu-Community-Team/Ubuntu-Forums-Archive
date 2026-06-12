---
title: "[SOLVED] Ubuntu on NEW Inspiron 530N"
date: 2007-10-24
forum: Dell  Ubuntu Support
---

### Post by iflanery on 2007-10-24
So I just got my new Inspiron 530N today. Got pretty much everything set up without much problem. Internet works, sound works, all that. Like most of you, however, I'm having a hell of a time getting the appropriate screen resolution set up (should be 1440X900). Installing the driver from the NVIDIA website doesn't work, as I can't get it to stop X. Searching online for answers hasn't been much help, either, as I keep getting referred to answers that don't apply to me in one form or another. ](*,)

My video card is an NVIDIA GeForce 8300GS (which, not surprisingly, is not supported).

Thanks in advance for any answers.

---

### Post by iflanery on 2007-10-24
Nevermind; the problem has been solved after much handwringing. The more I searched around the forum, the more I heard about Envy. I downloaded it, installed it, and was able to tick my appropriate screen resolution.

---

### Post by gbrainin on 2007-10-24
We have two 530Ns, one with the 8300 and one with the older 7300.  It appears that the 8300 is not recognized by Feisty, so it doesn't even give you the option of loading the restricted driver (this option is available with the 7300), leaving Envy as the easiest option for getting the proper driver loaded.

I suspect (have not confirmed yet) that this difficulty will go away in Gutsy.  Also note that I have read that if you're not doing a fresh install, it is important to undo all the changes that Envy does before upgrading.

---

### Post by iflanery on 2007-10-24
> **gbrainin said:**
> We have two 530Ns, one with the 8300 and one with the older 7300.  It appears that the 8300 is not recognized by Feisty, so it doesn't even give you the option of loading the restricted driver (this option is available with the 7300), leaving Envy as the easiest option for getting the proper driver loaded.

I suspect (have not confirmed yet) that this difficulty will go away in Gutsy.  Also note that I have read that if you're not doing a fresh install, it is important to undo all the changes that Envy does before upgrading.

Thanks for the heads-up. Now my problem is saving my settings to the x.org config file. The message I get is "Unable to remove old X config backup file /etc/X11/xorg.conf.backup". Any ideas as to how to solve this?

---

### Post by gbrainin on 2007-10-24
> **iflanery said:**
> Thanks for the heads-up. Now my problem is saving my settings to the x.org config file. The message I get is "Unable to remove old X config backup file /etc/X11/xorg.conf.backup". Any ideas as to how to solve this?

   I have never seen this error message.  Are you modifying the file using sudo?  Are the permissions on the backup file honked up somehow?  Just guessing.

---

### Post by iflanery on 2007-10-24
I wasn't modifying it with root access. Later on, I decided to use nano to edit the file, wherein I found three screen resolutions. Since I didn't want to mess things up on my system, I decided against trying to modify it.

---

