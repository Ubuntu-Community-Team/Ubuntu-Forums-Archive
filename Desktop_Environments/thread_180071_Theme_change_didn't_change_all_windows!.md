---
title: "Theme change didn't change all windows!"
date: 2006-05-21
forum: Desktop Environments
---

### Post by d_e_monat on 2006-05-21
I changed my theme to a dark one.

When I clicked System > Administration > Login Screen Setup, the window was the old theme.

Other "Admin" windows are doing same.  Haven't had time to check all.

Any ideas ](*,)

---

### Post by Fass on 2006-05-21
Applications run as root will not have their themes changed if you only change the theme for your user. To have the root theme be consistent with your user's, do this:

```
sudo ln -s /home/<insert your username here>/.themes /root/.themes
sudo ln -s /home/<insert your username here>/.icons /root/.icons
sudo ln -s /home/<insert your username here>/.fonts /root/.fonts
```

---

### Post by Nonno Bassotto on 2006-05-21
[http://www.ubuntuforums.org/showthread.php?t=77694&highlight=root+theme](http://www.ubuntuforums.org/showthread.php?t=77694&highlight=root+theme)

Section 4

---

### Post by d_e_monat on 2006-05-21
Oh boy, oh boy.  :mrgreen: 

That was fast and acurate!

I don't ask for help often because I can read!  I do apreciate the help on this one.

Here's a screen shot of what I have goin' on.

Dave

---

### Post by d_e_monat on 2006-05-21
Oops do over.

---

### Post by Fass on 2006-05-21
Nice, but too dark and green for me. :)

---

