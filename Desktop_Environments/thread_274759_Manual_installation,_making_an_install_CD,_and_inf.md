---
title: "Manual installation, making an install CD, and info about packages."
date: 2006-10-10
forum: Desktop Environments
---

### Post by imaginos on 2006-10-10
I had installed (by using Add/Remove) several packages that I need for everyday use.
Ubuntu 6.06 stores backup of all those packages in:
/var/cache/apt/updates

Is it possible to put them in some other directory (or even CD) and make a script that will install them all. That would be very nice if I have to reinstall system or put those packeges on another computer. It will also save me a lot of time/money, and it would be nice to make a CD that will be recognized by Add/Remove program (or Synaptic?). BTW, is Add/Remove same as Synaptic, and if not so, what are the diferences?

What about dependecies? I see that a package installed vvie Add/Remove also brings some other .deb packages with itself. If I manually install a package like this:
dpkg package_name (assuming that package_name.deb file is present in current dir)

What will happen to dependencies if they are also in that directory? Is their installation going to be automatically invoked by installing package that is dependent of them, or I will have to start them one by one.


I would like to learn more about packages and installation procedure, in terms of what happens when an installation starts, structure and content od .deb files, etc?


Also, what Add/Remove actually does? Does it starts:
dpgk package
in the background? Where Ubuntu keeps information about installed programs?


Thank you.

---

### Post by MetalMusicAddict on 2006-10-10
If your a handy person with linux Id look into [Reconstructor]("http://reconstructor.aperantis.com/index.php?option=com_frontpage&Itemid=1").

---

### Post by imaginos on 2006-10-10
Thank you!

Unfortunatley, I am not a handy person, but I am trying to become. :) I still don't understand theory about this topic (packages), so I am trying to learn about it...

---

