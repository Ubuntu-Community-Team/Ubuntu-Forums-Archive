---
title: "Effects + fglrx + ati M300 = HOWTO"
date: 2007-04-21
forum: Desktop Effects &amp; Customization
---

### Post by derrekito on 2007-04-21
Anyone have an up to date howto on getting compiz to work with the fglrx driver?  

When I try to enable the effects I receive a composite manager error, enabling composite in xorg.conf breaks the driver; so any ideas?

---

### Post by orange2k on 2007-04-21
Are you using Feisty?

Cause if you are you can probably install the best driver by going to system - administration - restricted driver manager.

Thats how I installed my nvidia driver anyway - very easy and very fast - go Feisty!!!
And I have a cheap MX-4000 AGP card, so I was very suprised to get Beryl up and running...

I`m not sure if it is that easy with your ATI...

---

### Post by derrekito on 2007-04-21
Yes I'm running feisty, and I am also running the latest proprietary drivers from ATI, and they are working.  But still composite error with compiz.

---

### Post by orange2k on 2007-04-21
Well it worked for me... but I must admit the effects that come with Feisty were quite slow...

So I tried beryl and wow, much much faster than compiz

Maybe installing Beryl would work...

---

### Post by derrekito on 2007-04-21
from the threads I read up on, Beryl pushes out a similiar error.  I need to get a work around for the composite manager in the fglrx driver.

Edit: I was right:

$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

---

### Post by ionman on 2007-04-21
Unfortunately the ATi proprietary (restricted) driver (the fglrx driver) does not support the composite extension. You need this extension in order to run Beryl/Compiz. There is a way to get it to work, but you need to install XGL. You can find out more info at [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL") Hope this helps!

-ionman

---

### Post by derrekito on 2007-04-21
> **ionman said:**
> Unfortunately the ATi proprietary (restricted) driver (the fglrx driver) does not support the composite extension. You need this extension in order to run Beryl/Compiz. There is a way to get it to work, but you need to install XGL. You can find out more info at [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL") Hope this helps!

-ionman

YOU ARE TOO COOL!  I got it to work, sorta.  Now beryl is spitting this out: 
```

** (beryl-manager:3043): CRITICAL **: can't execute beryl-xgl: Success

```

and it the message just loops.

EDIT:  

I was wondering if anyone knew if it is possible to get compiz working with emerald?

---

### Post by derrekito on 2007-04-21
bump

---

### Post by derrekito on 2007-04-22
bump :(

---

### Post by ionman on 2007-04-23
Sorry. Haven't checked this thread in a few days.

I don't know about running Compiz and Emerald. Compiz uses CGWD themes and Beryl uses Emerald themes (as well as others, with the proper extensions). If you are looking to install Emerald just do a:

> sudo apt-get install emerald emerald-themes

in the terminal. It will ask you for a password, and then install Emerald and the themes package.

Hope this helps!

- ionman

---

### Post by derrekito on 2007-04-23
> **derrekito said:**
> YOU ARE TOO COOL!  I got it to work, sorta.  Now beryl is spitting this out: 
```

** (beryl-manager:3043): CRITICAL **: can't execute beryl-xgl: Success

```

and it the message just loops.


bump

---

### Post by mapas on 2007-05-01
same here :(

---

### Post by derrekito on 2007-05-01
> **mapas said:**
> same here :(


any more info?

---

