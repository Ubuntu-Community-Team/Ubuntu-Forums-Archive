---
title: "[SOLVED] how do i un-install a package installed from tar.gz?"
date: 2008-12-20
forum: General Help
---

### Post by cb34 on 2008-12-20
how do i un-install a package installed from tar.gz?

i installed flash using the tar.gz from adobe's site, now i want to reinstall firefox and flash due to some problems i'm trying to hunt down.

in synaptic, flash-non-free is not ticked like it is installed, because i installed flash with the script that's included with the flash10 tar.gz download, and it's not showing in synaptic in local packages where my non-repo installed stuff shows up like where xwinwrap shows up.

so now after installing flash from a adobe script in the downloaded tar.gz..

how do i totally purge the install now. i've been an apt-get whore, haha:p uninstalling a non apt-get program is beyond me at the moment.

please help.. THANK YOU!

---

### Post by kerry_s on 2008-12-20
the flash script just copies the file to ~/.mozilla/plugins
you should have read what it was doing during the install when it asks you to continue.

open your file manager> press ctrl+h, click .mozilla, delete plugins.

---

### Post by cb34 on 2008-12-20
thank you.. i do read everything.. and i know about that dir, i was just kinda wondering..

is that libflashplayer.so the only file for flash... i was thinkin about deleting it, but thought maybe there was more to it than that..

anywayz.. thanks man!

and do you happen to know what the .macromedia dir is all about.. also flash?
where'd it come from i wonder? and it seems to hold lots of cached flash files i viewed recently? looks like it's just a cache dir for flash content? or some kinda per site settings.. hmmmmm?

can i delete the .macromedia dir to keep things clean ya think? looks like there's nothin special in there...

---

### Post by kerry_s on 2008-12-20
yes, you can delete both .adobe and .macromedia, there just settings and cache, they will be recreated again when flash is used.

---

### Post by cb34 on 2008-12-20
Thanks again kerry_s. done and done, mission accomplished. :D

you da man.

---

