---
title: "Trouble installing AWN Manager"
date: 2007-12-11
forum: Desktop Effects &amp; Customization
---

### Post by zabyss on 2007-12-11
I've been struggling with the installation of AWN for hours, trying two different versions and getting nowhere. Finally it is running, however I am still unable to install the awn-manager. I tried terminal commands "sudo apt-get install awn-manager"  it couldn't find the package, even after updating. I found the package on packages.ubuntu.com, but I'm getting a conflict that is not allowing the installation. It is trying to overwrite "usr/share/avant-window-navigator/awn-manager/window.glade". How might I go about fixing this?

---

### Post by LaRoza on 2007-12-11
[http://wiki.awn-project.org/index.php?title=Installation](http://wiki.awn-project.org/index.php?title=Installation)'

Copy and paste commands for Feisty, it should be easy.

---

### Post by zabyss on 2007-12-11
It *should* be easy.  Those are the instructions I used, although I'm running Gutsy.  I just tried the Feisty instructions, and it can't find the packages which is what it said when I tried to install the manager before through the terminal.  If I just try to install the manager, it tells me   

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  awn-manager: Depends: avant-window-navigator (= 0.1.9-1+bzr20071006~3v1ubuntu0)
E: Broken packages


Nothing is as easy as it should be...

---

### Post by Tristam Green on 2007-12-11
remove the package you installed and try this, if you're using Gutsy.

I followed the how-tos in this forum previously and never could get AWN working at all.

I found the wiki today, and it worked like a charm.

[http://wiki.awn-project.org/index.php?title=DistributionGuides#Reacocard.27s_Ubuntu_Gutsy_Repository](http://wiki.awn-project.org/index.php?title=DistributionGuides#Reacocard.27s_Ubuntu_Gutsy_Repository)

Best of luck

---

### Post by zabyss on 2007-12-11
I removed and then reinstalled everything, but I had to go through synaptic.  Going through terminal told me that it could not find the packages.  I installed everything from synaptic except the awn-manager, which has been the problem all along.  Still, it tells me it can't install it because

awn-manager:
 Depends: avant-window-navigator (= 0.1.9-1+bzr20071006~3v1ubuntu0)

What am I missing here?

---

