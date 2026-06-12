---
title: "[SOLVED] 8.4.1 + GDM login issues"
date: 2008-07-08
forum: Desktop Environments
---

### Post by Darth_tater on 2008-07-08
I recently installed 8.4.1 on my 3200+ and for some reason, I cannot login.  After the install finishes, I restart and go to login... GDM accepts my credentials and plays the login sound, then the screen goes dark for a second, and I get kicked back to the login window.

I had this same problem trying to install (I was using the 'try first' option...) the only way I got to install ubuntu was to select the install option directly from the boot menu.  

Because the screen blanks out, I believe this might have something to do with X.  this box has onboard graphics, and I think they are driven by an ATI chip.  Could a driver issue be causing the problem?  Thanks for your help.

Ps:  is there any way I can force the box to boot using VESA drivers?  Im thinking from the grub window…but I don’t know how to set that kernel parameter.  

&#61550;	Thanks again!

---

### Post by sayakb on 2008-07-08
Press F10 at login screen and click **Select Session.** Select Failsafe Gnome as your session. See if you can log in..

---

### Post by Darth_tater on 2008-07-08
YES!  that worked!  thanks so much.

what does this mean?  i assume the video driver didn't change.. so what changed to give me a successful login?

---

### Post by sayakb on 2008-07-08
Failsafe disables a couple of things. Try setting desktop effects to None and try logging in normally.

---

### Post by Darth_tater on 2008-07-08
will do.... i didn't know they were enabled by default.

i checked... it wasnt enabled.  was that because i am logged in under gnome fail safe?

---

### Post by Darth_tater on 2008-07-11
Well, everything is working now... so i guess i just had to manually start the fail safe session and disable visual effects.

- thanks all

---

### Post by sayakb on 2008-07-11
Np. Please mark the thread as solved.

---

### Post by Darth_tater on 2008-07-11
will do.

---

