---
title: "nvidia driver problem"
date: 2008-12-27
forum: General Help
---

### Post by qwertymodo on 2008-12-27
Under Ubuntu 8.04.1 Hardy, I never had any problems with the nvidia driver (version 177 I think) on my HP laptop.  However, about a month after upgrading to 8.10, the nvidia driver ceased to work.  It's been awhile since, so I don't remember all of the details, but I believe it may have been related to an update.  I booted and received an error, something about being unable to parse the xorg.conf file.  I had the system rebuild the file and it gave me a generic configuration with the driver disabled, which disabled all of my desktop effects and limited my resolution to 800x600... which is a pain because the laptop screen is widescreen.

  Basically, this deactivated the driver so I reactivated it and back to the error.  Then I went and tried totally reinstalling the driver and it didn't work.  I tried getting the driver from nvidia.com and running it from a root recovery terminal and that put me back to the same error.

  So then I went and did something stupid, I opened synaptic and did a quick search for nvidia-glx and purged everything that came up, with the intent of reinstalling everything and hoping the purge would clean it up.  However, apparently I missed something, because now I go into restricted hardware drivers and the nvidia drivers don't show up at all!  I used to have 2 or 3 different versions in the list, now the only driver in the list at all is my Broadcom wireless driver :(.

  So for the last month or two I've gotten along with the generic drivers, but now I'm fed up.  I now have two problems:  the original driver problem (no, I don't have the original xorg.conf for review, sorry...), and now, the drivers aren't even showing up.

  Help?

---

