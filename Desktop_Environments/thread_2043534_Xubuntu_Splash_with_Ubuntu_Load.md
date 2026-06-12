---
title: "Xubuntu Splash with Ubuntu Load"
date: 2012-08-16
forum: Desktop Environments
---

### Post by Petro Dawg on 2012-08-16
I recently installed the Xfce desktop environment through terminal in Ubuntu2D.  I just wanted to see how Xfce performance compared.  I logged into it once and now when I turn my laptop on or off I always see the Xubuntu loading/closing splash screen no matter which desktop environment I log in to (or out of).   

Is there a setting, or terminal command that can restore the standard Ubuntu loading screen (the one with the five dots that fill up as my computer loads/closes)?  

It's not critical, I just don't prefer seeing the xubuntu logo every time I use ubuntu .

I use Ubuntu12.04 btw in case it matters.

Thanks in advance for any help.

---

### Post by Moose on 2012-08-16
Go to your Xfce settings and there will be an option for splash. You can select no splash. I had XFCE aswell and never had that problem but also i never used one of their splash screens. PM me if this solution works.
 
-Anarchy

---

### Post by Petro Dawg on 2012-08-16
> **AnarchyTech said:**
> Go to your Xfce settings and there will be an option for splash. You can select no splash. I had XFCE aswell and never had that problem but also i never used one of their splash screens. PM me if this solution works.
 
-Anarchy

Didnt' work.

I must be using the wrong terminology, I checked the splash settings in Xfce and it was already set on "NONE".   Thanks for the suggestion though.

Its just the Xubuntu load screen that has the central bar which fills up while OS loads that I can't get rid of.   For Ubuntu it should be a purple background with the 5 or 6 dots that fill up.   For some reason I can't get the dots back.

---

### Post by Krytarik on 2012-08-16
Please see my earlier post here:

[http://ubuntuforums.org/showthread.php?p=11729473#post11729473](http://ubuntuforums.org/showthread.php?p=11729473#post11729473)

Regards.

---

### Post by Petro Dawg on 2012-08-16
> **Krytarik said:**
> Please see my earlier post here:

[http://ubuntuforums.org/showthread.php?p=11729473#post11729473](http://ubuntuforums.org/showthread.php?p=11729473#post11729473)

Regards.


The following worked like a charm...


> To set the Plymouth boot splash to the default one, run:
   ```
  sudo update-alternatives --config default.plymouth 
```
Then choose "ubuntu-logo.plymouth", followed by:
   ```
  sudo update-initramfs -u 
```
Thanks

---

### Post by Moose on 2012-08-17
Ok thanks for letting me know man.
 
-Anarchy

---

