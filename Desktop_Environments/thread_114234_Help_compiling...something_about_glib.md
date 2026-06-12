---
title: "Help compiling...something about glib?"
date: 2006-01-08
forum: Desktop Environments
---

### Post by Leiki on 2006-01-08
Hi all,

I've been using Ubuntu for about 2 days now and I just love it. I even deleted Windows! I've learned a lot about using the terminal and such in these past 2 days, and I probably need to learn a lot more, but hey...Ubuntu is very easy and fun!

Anyway, I want to install gFTP, so I downloaded the tar.gz file, extracted it into a folder in my desktop, and now I'm at the configure part. I type in ./configure and it goes through all of this stuff and at the end it says "The glib-config script installed by GLIB could not be found". I've searched a lot and couldn't find anything.

Well, you can see everything I typed here: [www.freepgs.com/tajeko/config](www.freepgs.com/tajeko/config) .

Any help would be very appreciated. Thanks!

---

### Post by kaamos on 2006-01-08
You can install gftp with synaptic. It's a lot easier. :)

[https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)

If you still want to compile: search synaptic for glib and look for packages that end with -dev. You need these developement libraries to compile.

---

### Post by Leiki on 2006-01-08
Oh, thank you so much! Worked perfectly. I know about the package manager, but I like to do things old school ;). Plus it's good to know when I want to install software not listed on the PM. Thanks again.

Edit: Assuming that the software I install using the terminal doesn't show up with the package manager (as with gFTP), is there any way to uninstall using the terminal in the future?

---

### Post by mo_x on 2006-01-08
See the manual pages for apt-get and dpkg.

---

