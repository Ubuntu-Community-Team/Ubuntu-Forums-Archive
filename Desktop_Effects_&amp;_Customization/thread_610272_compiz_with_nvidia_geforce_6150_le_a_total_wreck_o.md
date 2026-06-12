---
title: "compiz with nvidia geforce 6150 le a total wreck on gusty"
date: 2007-11-11
forum: Desktop Effects &amp; Customization
---

### Post by ZaphodNE on 2007-11-11
I thought I knew computers...I was wrong.  I search these threads and find nothing but happy compiz users.  I'm not one of them.

Compiz will not work.  Windows cannot be dragged.  Effects do not function.  The max / min / close buttons are gone.  No window theme whatsoever.  Yes, the freaking driver is there as per Restricted Drivers yada yada.  What the hell am I doing wrong?  I am completely out of ideas.  I've been at this since day 1 of gutsy....what am I missing???

:frown:

---

### Post by snkmad on 2007-11-11
Is it a desktop pc or a notebook?
I have an onboard geforce 6100, and it works great.
And the nvidia driver recognizes it as "geforce 6150" but i havent any issue with that so far.

---

### Post by ZaphodNE on 2007-11-11
Hello....it is a desktop....dell c521 dual core.

I feel it is a driver problem.  But gutsy reports the driver is correct and is being used.

Thank you for your reply....any and all help is appreciated.

---

### Post by eagle63 on 2007-11-11
> **ZaphodNE said:**
> I thought I knew computers...I was wrong.  I search these threads and find nothing but happy compiz users.  I'm not one of them.

Compiz will not work.  Windows cannot be dragged.  Effects do not function.  The max / min / close buttons are gone.  No window theme whatsoever.  Yes, the freaking driver is there as per Restricted Drivers yada yada.  What the hell am I doing wrong?  I am completely out of ideas.  I've been at this since day 1 of gutsy....what am I missing???

:frown:

I'm with ya.  I just upgraded to Gutsy a few days ago, and I can't get Compiz to work.  Desktop PC, Pentium 4, Nvidia 5200FX using the nvidia-glx drivers.  Actually, I can enable Compiz - but soon as I do the windows all lose their title bars.  Based on your description, it sounds like you're seeing the same thing.  After some searching around here, it seems like there's quite a few people with this problem.  

If you take a look at this link: [http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

you'll see a "troubleshooting" section where the author specifically talks about the missing title bar problem.  However, I've tried his solution with no luck.  He says to install nvidia-xconfig.  Well apt-get won't let me install that without also UNinstalling nvidia-glx.  (my video driver)  So that's obviously not right.  

I too am frustrated.  I could understand having flaky problems like this if I was using an ATI card or maybe some crappy built-in integrated video.  But this is happening with Nvidia hardware!  Did anyone test this stuff first before releasing it??

---

### Post by ZaphodNE on 2007-11-11
Eagle...dude....thank you!!....I thought I was losing my mind.  I mean, I do computers for a living, but this stupid s**t is just killing me!!  Yes, sounds like we have exactly the same misbehavior out of Compiz.

I am sorry you are in this boat as well.  Thanks for the link...i'll have a look for certain.

Yeah, testing.....maybe Canonical ought to rethink these "everything-6-month" releases, since it seems like the rest of the open-source world have day jobs and can't quite keep up the pace.

Again, thank you!!

---

### Post by eagle63 on 2007-11-11
> **ZaphodNE said:**
> Eagle...dude....thank you!!....I thought I was losing my mind.  I mean, I do computers for a living, but this stupid s**t is just killing me!!  Yes, sounds like we have exactly the same misbehavior out of Compiz.

I am sorry you are in this boat as well.  Thanks for the link...i'll have a look for certain.

Yeah, testing.....maybe Canonical ought to rethink these "everything-6-month" releases, since it seems like the rest of the open-source world have day jobs and can't quite keep up the pace.

Again, thank you!!

Hey no prob, hopefully this gets figured out.  I just was taking a look through another thread discussing this same problem, and there were a few people who fixed it by changing the "DefaultDepth" in the screen section of their xorg.conf file to "24".  Mine is already it 24, so no luck there - but you might want to check yours just in case that does the trick.

---

### Post by ZaphodNE on 2007-11-11
Hello again....I'm exactly where you are.  Checked the link you gave....got the same results you had.....arrrrrrrrrgh!!

I guess I shouldn't be dwelling on this like I am, because the OS really does work well and I can do anything I need to do.  I just want the fun stuff!!!!

Thnaks again....I'll keep digging and let you know if I find something.

---

### Post by snkmad on 2007-11-11
I dont have the same problem as you guys are having.
When you enable compiz, the windows loose their title bars?
This problem is related to emeral, the window decorator.
I dont use it here, thus i dont have problems.

I may suggest you guys switch to GTK window decorator until you find a real solution for this.

---

### Post by eagle63 on 2007-11-11
Ok, good news - I think I fixed it.  Going back again to another thread, someone posted a copy of their xorg.conf.  In the "device" section, they had the following 4 lines:

> 
Option "XAANoOffscreenPixmaps"
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
Option "AllowGLXWithComposite" "true"


I have no idea what these do, but I figured what the heck - why not throw them in mine and see what happens.  Result?  I have title bars back!!  And my terminal window is no longer a blank white box!  

SNKMAD - I keep hearing people talk about Emerald, but to be honest I have no idea what that even is.  To my knowledge, I haven't specified a window decorator anywhere.

---

### Post by ZaphodNE on 2007-11-11
Hi,

Kinda know what Emerald is.  There's a competitor to Compiz called Beryl.....tried it b4 and it's actually pretty cool.  Emerald is the window decorator that sort of 'plugs into' Beryl, as Beryl does all the work......at least this is my extremely limited understanding.

I read the previous post from the guy talking about Emerald, but found no evidence of Emerald on my machine.  I'm going to run with what you found.  You are clearly better at finding answers than I am.....kudos to u.

Thanks for hanging with me.  Really...Thanks!

---

### Post by ZaphodNE on 2007-11-11
eagle.....NICELY DONE!!!!!!!!!!!!   Things are working nicely!!!

I'm very curious to know where, and how you found those xorg.conf entries.  Again, you are way better than I at finding stuff.

YOU ARE DA MAN!!.....hope to run across you again sometime.

Dave

---

