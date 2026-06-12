---
title: "how should I install these?"
date: 2009-01-16
forum: General Help
---

### Post by Universal344 on 2009-01-16
I recently installed Istanbul screen recording software and after having trouble with it working  concluded the problem was that I did have the requirements listed on Istanbul Screen recorder's site:

GStreamer 0.10
Gst-plugins-base 0.10
PyGTK 2.6
Gnome Python Extras >= 2.11.3
Gst-python 0.10
python-xlib

how should I go about installing these?

---

### Post by Nepherte on 2009-01-16
Look for the programs in synaptic. If you are trying to install Istanbul screen recording by compiling it manually, you should pick the *-dev packages.

---

### Post by taurus on 2009-01-16
See if they are available from the repos, System -> Administration -> Synaptic Package Manager -> Quick Search.

---

### Post by logos34 on 2009-01-16
but those pkgs are dependencies--you can't uninstall them without doing the same for istanbul.  Edit: 

or did you mean by this:

> **Universal344 said:**
> concluded the problem was that I did have the requirements listed on Istanbul Screen recorder's site:
...

how should I go about installing these?

to really say you installed the source tar.gz istanbul, and did *NOT* have the reqs?

---

### Post by redseventyseven on 2009-01-16
Use the Synaptic Package Manager.

In fact, Istanbul is available in the Ubuntu repositories (you may need to enable the non-free ones first - you should be able to find out how to do that by googling), so you should probably use Synaptic to install that and it'll take care of the dependencies itself.

You may also need the medibuntu repositories enabled (these are disabled by default to get round a few legal issues) - again, googling this should give you instructions on how to do it.

---

### Post by Universal344 on 2009-01-17
Ok, so can I just go to synaptic check Istanbul and click OK to any other packages that need to be installed?  And also, what are these legal issues mentioned above? Isn't all software in the repos (main, restricted, universe and multiverse) perfectly legal?  Should I check back before I download any packages that istanbul depend on, or can I assume they are all fine?

---

### Post by Universal344 on 2009-01-17
When I checked Istanbul it told me it also needed to install gettext, python-gnome2-extras and python-xlib, can I go ahead and mark them all for installation?

---

