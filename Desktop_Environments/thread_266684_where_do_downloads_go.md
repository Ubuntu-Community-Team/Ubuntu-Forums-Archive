---
title: "where do downloads go?"
date: 2006-09-27
forum: Desktop Environments
---

### Post by oilchangeguy on 2006-09-27
hi, i'm new to the linux world and am trying to learn about a number of things. 1st is how to do downloads, for example trying to install the full version of openoffice from openoffice.org. in windows this would be a very easy download and install. in linux not so. when the download is completed where does it go, and how do i find and install it? thanks for any help.

---

### Post by jocko on 2006-09-27
> **oilchangeguy said:**
> hi, i'm new to the linux world and am trying to learn about a number of things. 1st is how to do downloads, for example trying to install the full version of openoffice from openoffice.org. in windows this would be a very easy download and install. in linux not so. when the download is completed where does it go, and how do i find and install it? thanks for any help.

Well, openoffice is installed by default in Ubuntu, so there is no need to download anything.

---

### Post by zvacet on 2006-09-27
It goes where you told him to  go(personal map,home, desktop...).Install it with wright click(you will see dropdown menu and gdeb installer).You can also install it with synaptic manager.All you download goes to /var/cache/apt/archives.

---

### Post by oilchangeguy on 2006-09-27
i know a version of open office is installed, and i'm just using this as an example of how to find out where downloads go. the pre-loaded version does NOT contain everything that's in version 2.0.3. now if someone could kindly answer my question without telling me it's already installed. thanks.

---

### Post by crossedout on 2006-09-27
Well, I usually choose where I want files downloaded, but if I'm not mistaken by default files d/l to your home directory (/home/<username>).

As far as OO goes, jocko speaks the truth.

-Xout

---

### Post by jocko on 2006-09-27
> **oilchangeguy said:**
> ...now if someone could kindly answer my question without telling me it's already installed. thanks.

Sorry, I think I misunderstood you.
If you start a download from firefox, it will end up on your desktop.

---

### Post by cmost on 2006-09-27
Technically, programs downloaded via Apt (Synaptic) are stored in /var/cache/apt/archives for a time.  As a newcomer to Linux, and especially to Debian Linux (Ubuntu's parentage is Debian) you should come to understand that programs are installed and updated completely differently than in Windows.  In Windows, there is no central database which keeps track of which programs are installed on your system, theier version number, etc.  Sure, there is the "Add & Remove Programs" applet, but this is little more than an uninstall utility.  It does not offer the ability to upgrade your entire system like Apt for Debian.  That being said, you should avoid using packages (Linux's term for programs) from sources other than Synaptic.  Doing so risks breaking your system and introducing glitches.  Welcome aboard.

---

