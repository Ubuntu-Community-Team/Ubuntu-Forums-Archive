---
title: "Problem with Evolution Removal"
date: 2006-05-15
forum: Desktop Environments
---

### Post by strimackus on 2006-05-15
I seem to have done something fairly stupid.  I've been using Thunderbird for email, so I thought I'd remove Evolution using the package manager.  One of the packages I unistalled was the evolution-data-server, and I was informed that if I uninstalled this then there were a bunch of other packages I had to uninstall as well.  I assumed this would be no problem and didn't even bother to really look at what these packages were, however this seems to have been a big mistake.

Now, when I start up my computer I get to the login screen but once I log in I just get a blank brown screen.  So, I assume I've managed to uninstall some important GNOME package or something.  On top of this apt-get doesn't seem to have a log file so I can see what I've done.

If somebody could give me a list of the packages that are uninstalled via Synaptic Package Manager along with evolution-data-server, I'd really appreciate it.  Hopefully if I reinstall these from the command line everything will work again.

---

### Post by strimackus on 2006-05-15
Fixed it myself, it was ubuntu-desktop that needed to be reinstalled.

---

### Post by DonQuixote on 2006-05-17
Thanks for posting this.  I did the very same thing.

I don't understand why Evolution is so pervasive.

---

### Post by Danepak on 2006-05-23
I can't seem to uninstall Evolution without taking gnome with it, what am I doing wrong.  Newbie be kind.

---

