---
title: "Missing menu and side bar, Ubuntu 11.04"
date: 2011-06-28
forum: Desktop Environments
---

### Post by jfeeney on 2011-06-28
Hi all,

So I'm a newbie to Ubuntu and made the mistake of playing around with compiz settings, and did I ever mess up.  Using the graphical compiz editor, I accidentally switched it to default from compiz, and it took both the top bar and the left-side launcher menu away.  So I have no access to anything except my desktop, which is basically useless.

I created a terminal launcher from there and loaded up the graphical compiz editor again, and switched it back.  Still, the launcher menu and top bar are  missing.  I uninstalled compiz and unity, and reinstalled them, and still the menus are missing.  However, this is only in the default ubuntu login.

Thankfully, the classic menu, safe mode, and unity 2D desktops still load fine.

Any ideas?

Cheers,

---

### Post by trizrK on 2011-06-28
> **jfeeney said:**
> Hi all,

So I'm a newbie to Ubuntu and made the mistake of playing around with compiz settings, and did I ever mess up.  Using the graphical compiz editor, I accidentally switched it to default from compiz, and it took both the top bar and the left-side launcher menu away.  So I have no access to anything except my desktop, which is basically useless.

I created a terminal launcher from there and loaded up the graphical compiz editor again, and switched it back.  Still, the launcher menu and top bar are  missing.  I uninstalled compiz and unity, and reinstalled them, and still the menus are missing.  However, this is only in the default ubuntu login.

Thankfully, the classic menu, safe mode, and unity 2D desktops still load fine.

Any ideas?

Cheers,
type in the terminal:
[B]metacity --replace
[/B]that'll change to metacity temporarily.

---

### Post by Krytarik on 2011-06-28
jfeeney, please see this troubleshooting guide:
[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

Greetings.

---

### Post by Jacobonbuntu on 2011-06-28
> **jfeeney said:**
> Hi all,

So I'm a newbie to Ubuntu and made the mistake of playing around with compiz settings, and did I ever mess up.  Using the graphical compiz editor, I accidentally switched it to default from compiz, and it took both the top bar and the left-side launcher menu away.  So I have no access to anything except my desktop, which is basically useless.

I created a terminal launcher from there and loaded up the graphical compiz editor again, and switched it back.  Still, the launcher menu and top bar are  missing.  I uninstalled compiz and unity, and reinstalled them, and still the menus are missing.  However, this is only in the default ubuntu login.

Thankfully, the classic menu, safe mode, and unity 2D desktops still load fine.

Any ideas?

Cheers,

...I guess you disabled the Unity plugin (in Compiz settings) just log in in classic, open the Compiz settings (like you did before :P) and enable the Unity plugin again. your desktop might get scrambled a bit, but after a restart all should work fine,

have fun!
(and welcome!)

---

### Post by Krytarik on 2011-06-28
> **Jacobonbuntu said:**
> ...I guess you disabled the Unity plugin (in Compiz settings) just log in in classic, open the Compiz settings (like you did before :P) and enable the Unity plugin again. your desktop might get scrambled a bit, but after a restart all should work fine,
Compiz uses different profiles for Unity and classic Gnome, so you should try avoid a situation like this ;-) :
[http://ubuntuforums.org/showthread.php?t=1787781](http://ubuntuforums.org/showthread.php?t=1787781)

So, if you want to try this approach, make sure to switch to the "Unity" profile before enabling those plugin, and switch back to "Default" thereafter.

However, I advise using the guide I linked to earlier, because it also covers some other issues that may occur when messing up the Compiz settings.

---

### Post by jfeeney on 2011-06-29
> **Krytarik said:**
> jfeeney, please see this troubleshooting guide:
[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

Greetings.

Thanks everyone for the replies.  The guide that Krytarik posted to is a life saver and is really comprehensive.  Most of the "fixing compiz" discussions I found on my own only contained fragments of the information and were generally insufficient.

Thanks again!

---

### Post by Krytarik on 2011-06-29
You're very welcome! And thanks for the compliments! :-)

---

### Post by Jacobonbuntu on 2011-06-29
> **Krytarik said:**
> Compiz uses different profiles for Unity and classic Gnome, so you should try avoid a situation like this ;-) :
[http://ubuntuforums.org/showthread.php?t=1787781](http://ubuntuforums.org/showthread.php?t=1787781)

So, if you want to try this approach, make sure to switch to the "Unity" profile before enabling those plugin, and switch back to "Default" thereafter.

However, I advise using the guide I linked to earlier, because it also covers some other issues that may occur when messing up the Compiz settings.


oooops!

of course!! this is stupid....   :oops:
I remember I did it once (disabling the Unity plugin by accident), but still in the Unity-session I created a starter> *gnome-panel*, and reactivated the Unity plugin, after a restart the gnome panel wouldn't start and all was ok.

thanks for warning!

---

