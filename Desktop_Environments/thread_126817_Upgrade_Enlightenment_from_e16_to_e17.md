---
title: "Upgrade Enlightenment from e16 to e17"
date: 2006-02-07
forum: Desktop Environments
---

### Post by aaalunchbox on 2006-02-07
I'm running breezy with enlightenment 16, aka enlightened gnome.  It is great.  Yet i still want more.  I want to try to upgrade to e17 but i'm not too sure how.  I figured i would see if someone could give me a hand on what to expect before i go and break something thats already working :p  
I know about the repos to get e17 thru apt-get.  Now, i'm assuming its not as easy as installing e17 on top of e16. Or is it?  O.o

---

### Post by Mopatop on 2006-02-07
Hey

I'm afraid e17 is still in heavy development and my experience with pre-built Ubuntu repositories has been bad. The best and most stable way (amazingly) is to build e17 from CVS - that's the version the devs use and the devs hate broken WMs as much as we do :-)

The way I do it (at work, no less) is using [get_e.sh]("http://dev.winged.it/download/enlightened_stuff/enlightenment_updater_script"). I warn you though, it's not for the faint of heart. You'll need to install a load of -dev libraries and be prepared for the build to not work first time at all.

-Rob

---

### Post by aaalunchbox on 2006-02-07
I will have to try that.  I'm doing this on my work computer too.  Speaking of which, its about quitting time.  I did find some info.  e16 and e17 can coinside, just not in the same directory.  I installed e16 from synaptic so i got to see where it stuck everything.  I think you can specify where to stick the e17 binaries and once installed, you can pick it out of the sessions list.  I THINK.  check [http://www2.get-e.org/Main/FAQs/#40](http://www2.get-e.org/Main/FAQs/#40)    It offers a little explination.  I'll try to look into it more tommorow.  Althought quick question, is engage supported in e16?

---

### Post by Ampersand on 2006-02-08
I think that Engage is based on the e17 libraries, so will probably require most of them to be installed. It might work in e16 once installed, though.

---

