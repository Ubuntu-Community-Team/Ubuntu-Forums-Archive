---
title: "Depends: kdebase-data (&lt; 4:3.5.11)"
date: 2008-11-25
forum: Desktop Environments
---

### Post by luckygerbils on 2008-11-25
I've been trying to install kde just to try it out, I'm getting weird problems.  After noticing that kicker and kcontrol didn't appear to be installed, I tried manually (apt-get install kicker kcontrol) installing and I keep getting this message:
> The following packages have unmet dependencies:
  kcontrol: Depends: kdebase-data (< 4:3.5.11) but 4:4.1.3-0ubuntu1~intrepid1 is to be installed
  kicker: Depends: kdebase-data (< 4:3.5.11) but 4:4.1.3-0ubuntu1~intrepid1 is to be installed
E: Broken packages
I'm not sure why they would require kdebase-data LESS than a certain version, but whatever.  I've tried removing Intrepid Proposed and all the other newer repos from /etc/apt/sources and reinstalling kdebase-data to see if I could get a lower version, but no dice.
How can I resolve this?

---

### Post by Achetar on 2008-11-25
in Synaptic click Reload. This will reload the application database.

Now find kde. double click it
next find kdebase-data double click it if it isn't already green.

Then install. It should download and install.

---

