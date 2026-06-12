---
title: "Help wanted by an amateur"
date: 2007-11-17
forum: Desktop Effects &amp; Customization
---

### Post by Newbie29 on 2007-11-17
I have the following graphic card:

ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]

Whenever I go to System>Pref.>Appearence  and go to visual effects and click on either "normal" or "extra" a window pops up saying "Error Desktop effects could not be enabled"

Please tell me how to enable the desktop effects.......

Again, I am not well-versed in Linux as such, so please simple instructions would be greatly welcomed.

Thanks in advance.

---

### Post by cam381 on 2007-11-17
Did you install the right driver in restricted driver manager? You should see an icon in the notification area. Click on it and install. If there is no drivers either upgrade card or wait for new driver. Hope that helps. :)

---

### Post by Newbie29 on 2007-11-18
No, I'm pretty sure the graphic card's drivers are working properly, cause when I type in a command in the terminal ( I don't remember what it was....) which I'd read somewhere, the reply was 

direct rendering:yes


So, I think that the driver is installed properly....

---

### Post by Goombie on 2007-11-18
I had this same problem yesterday, and I stumbled across a solution: 
Go to your /home/(username).gconf/apps/ folder, and look for a folder named compiz. Don't delete that folder, just move it to your desktop. Now try enabling desktop effects. If it works, then you can delete the compiz folder you moved. Good luck.:popcorn:

---

### Post by Forlong on 2007-11-18
What's the output of ```
compiz
``` in a terminal?

---

