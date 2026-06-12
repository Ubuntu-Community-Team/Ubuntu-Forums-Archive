---
title: "Reset screen resolution for user"
date: 2009-05-16
forum: General Help
---

### Post by bimaljr on 2009-05-16
Hi
I have changed my screen resolution and after that my screen displays "Out of Range".

I have some urgent work so I have created another user so can login and do my work. 

Now I want to start use my original account. I want to reset screen resolution for my original user account. 

Please describe me how to do this ?

---

### Post by Legace on 2009-05-16
Delete monitor.xml in **/home/[COLOR="Red"]YOUR_OLD_USERNAME[/COLOR]/.config**

Or copy monitor.xml from your current user's .config folder into the old user's .config folder.. :)

---

### Post by bimaljr on 2009-05-17
Thanks
This works.

---

### Post by Legace on 2009-05-17
> **bimaljr said:**
> Thanks
This works.

No problem :) Enjoy.

---

