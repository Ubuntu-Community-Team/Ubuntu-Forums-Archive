---
title: "HOWTO install beryl on Ubuntu Feisty with nVidia graphics card on Inspiron"
date: 2007-06-10
forum: Dell  Ubuntu Support
---

### Post by Balistic on 2007-06-10
I make this SIMPLE guide, so YOU the newbie, won't have to go through all the hassle I had to go through in order to get this thing to work.  Linux community is great, I appreciate everyone's support here, if this help at least one person, I'll be extremely happy...

DISCLAIMER: Just like with any other tutorial, though its tested and should be safe, if you choose to follow this instructions, you are doing it at your OWN risk!  (if that didn't scare you, you may continue...)

My system:
Dell Inspiron E1705 (aka 9400), T7200, nVidia 7900gs.  I think this method though should work on most other inspirons with an nVidia vid card.

ALL you have to do is this:
1. Fresh install of Ubuntu feisty fawn (7.04) -> to make sure a n00b like me didn't have a chance to mess anything.
2.  Make sure you're connected to the internet, if you didn't set up your wireless yet (I haven't..), just use a cable...  ==> If you don't have the latest drivers, the following steps might take a little while (depending how fast is your network) since your system will be downloading the latest drivers.
3.  go to System -> Preferences -> Desktop Effects, enter your password if prompt, enable desktop effects, agree to the 'risks' message (if you get one).  Now your system should start downloading the latest nVidia driver, and it'll also inform you that Desktop Effects won't be enable until you restart x (crtl+alt+backspace).  Once the new drivers have installed, restart your computer.
4. go to System -> Administation -> Restricted drivers manager and make sure your nVidia driver is enabled, if its not, enable it.
5.  go to System -> Preferences -> Desktop Effects, enable it, if all went well you should be able to use some basic effects now like window wobble, and cube effect (that's not beryl quite yet though).
6. If you're connected to the net, and your system is not up to date, you should be able to see an icon in the top right corner (next to the network and shut down icons) suggesting to update your system.  Do that!  Let it fully update your system, and once this is done, hit refresh to see if there are any other update available.  Keep updating until your system is fully up to date.
7. Restart your computer.

===Now, let's get Beryl...!  ===
8.  go to Applications -> Accessories -> Terminal and type there: ```
sudo apt-get install beryl beryl-manager emerald-themes
``` Hit Enter...
9.  Restart X (ctrl+alt+backspace) or just restart your computer if you reall want to..
10, go to Applications -> Accessories -> Terminal and type there: ```
beryl-manager
``` Hit Enter.
11.  Congratulations.  If all went well, you now have beryl up and running.  Wasn't that easy?!

CREDITS: The above is my own compilation of other peoples work, I just want to help my fellow newbies out there.  When writing the above I relied mostly on these 2 links:
[http://ubuntuforums.org/showthread.php?t=263851&page=186](http://ubuntuforums.org/showthread.php?t=263851&page=186)  (Namely post #1856)
and
[http://ubuntuforums.org/showthread.php?t=357501](http://ubuntuforums.org/showthread.php?t=357501) (Namely PriceChild's initial post)

Hope that helped..!

---

### Post by camarojones on 2007-06-10
YAY!!!!!!

IT'S ALIVE!!!!!!

Thanks for the tutorial. Worked great!

Thomas

---

### Post by Balistic on 2007-06-11
How do you get the cube to rotate like on the pics you've attached?  when I use ctrl+alt+arrow key I just get a simple cube flipping corners...

---

### Post by LollYouSuckZor on 2007-06-11
Dude! You are awesome!! It's finally working!!
BRAVO!

---

### Post by mikledet on 2007-06-11
Yessssssssssssssssssssssssss!!!! Thank you thank you thank you!
Finally I got this to work, great guide!  you're Da man!

**Mods maybe you should sticky this, it was VERY helpful.

:KS :KS :KS :KS :KS

---

### Post by xtang on 2007-06-11
> **Balistic said:**
> How do you get the cube to rotate like on the pics you've attached?  when I use ctrl+alt+arrow key I just get a simple cube flipping corners...

ctrl+alt+use the mouse to drag

---

### Post by LollYouSuckZor on 2007-06-11
Funny thing is, I think this tutorial has helped more people than the tutorials you find on google...

---

### Post by camarojones on 2007-06-11
Yes...Crtl+Alt+click and hold.

And to zoom the cube out....

Desktop>Rotate Cube>General>Zoom.

---

### Post by doepain on 2007-06-11
I got this working on my T41, ut I ave to lower my resolution to 1024x768... my graphics card (I believe is an ATI).

Do you think If I were to try and upgrade my drives I could use beryl in my desired resolution.

I can not even get Skydome working with my system.  I think my graphics Processor can't handle it (perhaps due to drivers).

---

### Post by mikledet on 2007-06-11
> **doepain said:**
> I got this working on my T41, ut I ave to lower my resolution to 1024x768... my graphics card (I believe is an ATI).

Do you think If I were to try and upgrade my drives I could use beryl in my desired resolution.

I can not even get Skydome working with my system.  I think my graphics Processor can't handle it (perhaps due to drivers).

What graphics card do you have?  And beside it is always a good idea to install the latest drivers.

---

### Post by doepain on 2007-06-11
I am not on that system now, but I know that it is an ATI Rage of some sort.

---

### Post by mikledet on 2007-06-13
How do I get beryl to work on KDE?  I manage to get the beryl-manager to run, but it doesn't do any effects..

---

### Post by imsorryidontdowindows on 2007-06-13
I have the new inspiron e1505 not nvidia and just installed beryl and its working. But how did you get the cube period. when i go ctrl-alt-arrow i just move desktop to desktop, but i have four enabled.

i used this to install.

Support for ATI cards
From Beryl Wiki
Jump to: navigation, search

Please make sure your card is supported for accelerated graphics. In a terminal type:

glxinfo | grep direct

If you get this output back, your card should work:

direct rendering: Yes

If you get a "no" from this test, please install the correct driver.


Driver install

Use the Feisty's RestrictedDriversManager to install the Graphics card drivers.


Install Beryl

Make sure you have multiverse [Repositories] enabled (Its on by default) and install using:

sudo apt-get install beryl beryl-manager emerald-themes

Run Beryl

Alt+F2 then Enter

beryl-manager


Add to Startup

Add beryl-manager to the list of startup programs, by going to System -> Preferences -> Sessions, and under the tab Startup Programs and clicking New. Enter for both Name and Command arguments beryl-manager.




> **camarojones said:**
> YAY!!!!!!

IT'S ALIVE!!!!!!

Thanks for the tutorial. Worked great!

Thomas

---

### Post by vco08 on 2007-06-16
I just install Desktop Effects, but its not in my menus. Any idea where its at? I went to System, but there is no Preferences.

---

### Post by waggygee on 2007-06-17
It works!! Cool!! But how do I get Beryl to start running when I startup Ubuntu

---

### Post by cml21 on 2007-06-17
Thanks for the tutorial.  WORKS GREAT!

---

### Post by ccfromnj on 2007-06-19
Thank You ! Thank You !:KS:KS

---

### Post by ccfromnj on 2007-06-22
> **ccfromnj said:**
> Thank You ! Thank You !:KS:KS

Do you have any problems returning form suspend or hibernate ?

---

### Post by luckyd on 2007-06-22
> **waggygee said:**
> It works!! Cool!! But how do I get Beryl to start running when I startup Ubuntu

You may have already figured it out, but anyways you go to system/preferences/sessions/ than you add beryl-manager as one of the applications to start when you login.

---

### Post by goofeyfoot on 2007-09-19
I tried the above and I still have the same problem.  Beryl won't load.  In the terminal I get this error:

Reloading options
beryl: Failed to load slide: /home/robb/hotcorners_racarr.svg
Segmentation fault (core dumped)

What the heck is this thing.  I don't have a robb hotcorners thingie and I don't know how to correct this problem.  I am going nuts.  Nuts I tell you.

Thanks.

Michael

---

### Post by Immorten on 2007-09-19
I get an error when writing beryl-manager. It says: Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Can anyone export their settings and upload somewhere? 

Greets

---

