---
title: "Takes an age to start"
date: 2007-10-20
forum: Desktop Environments
---

### Post by brim4brim on 2007-10-20
I've just performed a clean install of Gutsy and when I boot, it takes forever to load.  Initially I was not seeing a splash screen.

I read this is due to an incorrect resolution in usplash so I corrected that but no luck.

I read that if you disable the splash screen, at least you'd get some feedback that it was booting so I did that and edited menu.lst to comment out the quiet splash section.

Now everything seems to go fine when starting.  I get all Ok messages but when it goes to start Gnome login screen, I get a black screen for about half a minute.

I have no idea what is causing this!  Can someone help me?  I was using the default driver but now I'm using the restricted driver for my ATI X600 mobility but its the same with both drivers.  I'm guessing its a Gnome or X problem as everything seems fine until it tries to load the login screen.

---

### Post by sethtriggs on 2007-10-23
> **brim4brim said:**
> 
Now everything seems to go fine when starting.  I get all Ok messages but when it goes to start Gnome login screen, I get a black screen for about half a minute.
.

I'm having this same problem! My system particulars are in my signature. I will try to take off the splash screen for myself too.

-Seth

----

Now I boot great and this was after fixing my resolution!

[http://ubuntuforums.org/showthread.php?t=581075&highlight=usplash.con](http://ubuntuforums.org/showthread.php?t=581075&highlight=usplash.con)

It may be a problem with the resolution of your splash screen, (This would be problematic for me, for example, because this laptop has a widescreen monitor).

Follow that thread.

If you get stuck at a small resolution (like I did with 640 x 480), follow this thread:
[http://ubuntuforums.org/showthread.php?t=268190](http://ubuntuforums.org/showthread.php?t=268190)

Now for me everything is working perfectly.

-Seth

---

### Post by brim4brim on 2007-10-23
> **sethtriggs said:**
> I'm having this same problem! My system particulars are in my signature. I will try to take off the splash screen for myself too.

-Seth

----

Now I boot great and this was after fixing my resolution!

[http://ubuntuforums.org/showthread.php?t=581075&highlight=usplash.con](http://ubuntuforums.org/showthread.php?t=581075&highlight=usplash.con)

It may be a problem with the resolution of your splash screen, (This would be problematic for me, for example, because this laptop has a widescreen monitor).

Follow that thread.

If you get stuck at a small resolution (like I did with 640 x 480), follow this thread:
[http://ubuntuforums.org/showthread.php?t=268190](http://ubuntuforums.org/showthread.php?t=268190)

Now for me everything is working perfectly.

-Seth

Thanks for that.  I fixed the problem but it was weird.  I have a widescreen laptop 1280 X 800 resolution.  Ubuntu correctly detects this but USplash didn't.  It was 1280 X 768 so I fixed it but nothing.

The only that worked was disabling the splash in Grub and uninstalling USplash.  Even the correct resolution for USplash failed which is odd.

---

