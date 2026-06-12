---
title: "Compiz - Unity crash"
date: 2012-05-16
forum: Desktop Environments
---

### Post by praveenkumarpon on 2012-05-16
Hi, I am new to Ubuntu, sorry if I didn't get some Ubuntu terms right.
I did something with Compiz while customizing and hence the Unity taskbar, Unity dock crashed. Nothing is on the screen except the wallpaper.
Restart didnt help.

Now I'm using Gnome by changing it on the login screen. Comfortable with the Unity 2D shell available in Gnome.

Will the crash of Unity affect Ubuntu? Since I'm comfortable with using Gnome now, and since I may not be able to do some complex fixes to resurrect Unity, can I leave it as such?

Please advice,
Thankyou.

---

### Post by grahammechanical on 2012-05-16
You can carry on using Ubuntu 2D as it does not use Compiz as the window manager but Metacity.

What you can do when you are in Ubuntu 2D is open Compiz Configuration Settings Manager (CCSM) and try to undo what you changed. That may put things right.

Regards.

---

### Post by BLewis on 2012-05-16
Extra stuff:

Long time Ubuntu user (including Compiz and many dev builds and I have used Ubuntu since around 2008). First time I have searched the forums to contribute, but here goes :) :

If you have problems with Unity and don't mind losing the Unity config (i.e. transparency and all the rest, and note, I don't mean permanently, I mean your current settings, this basically just does a restore):

Just run this either in the application called terminal in the dash or by pressing Ctrl Alt T to launch that terminal or Alt F2 and then type:

unity --reset

KEY:

which should reset unity. Although, since it seems you might not be able to do any of these without Unity, you can just press **Ctrl Alt F1** (or any F-number, these are known as TTY 1, TTY 2, etc.) and login with your username and password and then run:

**DISPLAY=:0**

and then run **unity --reset** like I said before. (The display bit just means that while you aren't on an actual UI area, you want it to affect that...)

Extra stuff:

Hope this helps if you have any more problems please just ask. But some other things I would suggest trying if this fails:

Go to the TTY again (Ctrl Alt F1) and then run:

sudo apt-get purge nvidia-* (If you have an nvidia graphics card, since these often break things)

sudo apt-get install ubuntu-desktop nvidia-common (To reinstall the nvidia driver)

If you have other cards, please just look here: 
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)
Or just post and I will find out the exact details and write them for you. 

More information about Ubuntu I wish I had been told:

In your home folder, there are many ".something" directories which you cannot see because they are hidden (Pressing Ctrl H reveals them) and these hold the configurations settings for all of your applications along with some cache and other things, you can safely delete these without losing any actual data or any applications if you want to reset all your applications (including the core OS, so you will lose your background setting for example).

In case you don't know yet, Ubuntu operates using Superuser through sudo, this means that many applications will ask for your password and to run some commands in the terminal I introduced you to, you need to use the word sudo beforehand and then type your password.

---

### Post by BLewis on 2012-05-16
> **grahammechanical said:**
> You can carry on using Ubuntu 2D as it does not use Compiz as the window manager but Metacity.

What you can do when you are in Ubuntu 2D is open Compiz Configuration Settings Manager (CCSM) and try to undo what you changed. That may put things right.

Regards.

I wouldn't recommend this since CCSM is extremely buggy in itself and it is not even recommended or supported any more. Personally I would either try the rather complex fixes I suggested or stick with Ubuntu 2D. 

Although, having looked at your post more closely originally, it seems that because you can access a desktop, the quickest fix would be to just run Alt F2 and the type unity --reset inside Unity 2D which would screw up 2D a bit for a sec, but 2D should work fine on reboot and this should fix Unity (3D) properly too. :)

Gd luck.

---

### Post by praveenkumarpon on 2012-05-16
Thanks,
I did a Unity reset and its back to normal again.

Also, Gnome has this Application menu where you could see all installed apps right, isnt it possible to view all installed apps in Unity like you would do on an Android?

---

### Post by fudoki on 2012-09-18
Two quick questions and a comment:
1)  Why not just perform the Unity reset using the "Root Terminal" available in any other GUI than the broken Unity 3D?  Then you are already in the correct display, etc.
2)  What is your basis to make the remark "(If you have an nvidia graphics card, since these often break things"; and I'll bet you don't own an nVidia card...  People who make remarks like this usually don't actually own an nVidia card, the most reliable, highest performance video cards available.  If Unity was working correctly before Compiz flaked out - which it does chronically - that would be de facto proof the nVidia drivers are correctly installed and working.  Otherwise there would be a black screen, or an "Out of Range" message.  I would not re-install the video drivers, regardless the card type, when doing a reset of Unity unless I was 100% sure there was a video driver issue, and if it was working correctly, and is still working (you are seeing a picture) you can bet the video drivers have not changed.  It's Compiz that's so totally breakable, right?

One cannot help but wonder if these Gnome "3" interfaces are being pushed out the door before they are ready.  Both Unity, and Cinnamon, look great but break reliably after just a few weeks use and the cause is generally impossible to find, troubleshoot, or fix.  So you have Linux taking the Windows path of "complete re-install", "you'll have it OUR WAY", and "you don't dare touch a thing regardless your level of expertise".  This IMHO is a cop out, people like Linux because it works and if it breaks you can find out why and fix it.  If Unity is not ready for prime time, it should stay in development until it is.  Suggesting a user just "stay with Unity 2D" may be the best advice with a broken "headliner GUI", but it's bad for Linux.

I agree about trying to back out changes in Compiz - it will only get worse.  The reset is all you can do...

---

### Post by WierdKid on 2012-12-26
I've had computers with both NVidia and ATI, and I've used both Intel and AMD processors, and from my experiance, I have had nothing but problems with my Intel/NVidia systems, where my ATI/AMD systems have been outstanding.

Regardless, I want to thank BLewis for the fix. I was getting no DE trying to run Unity (I'm on 12.10 and don't see any option for 2D vs 3D), and this cleared it up for me.

---

