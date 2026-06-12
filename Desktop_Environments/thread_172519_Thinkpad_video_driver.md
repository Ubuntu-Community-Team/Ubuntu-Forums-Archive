---
title: "Thinkpad video driver"
date: 2006-05-08
forum: Desktop Environments
---

### Post by abk on 2006-05-08
Hey,

I'm a sorta-kinda-newcomer to Linux, and Ubuntu is my distro of choice. I'm quite familiar with OS X (I work in a Mac repair shop), so I have some basic UNIX command knowledge, but I'm still getting used to Linux and all of its interesting bits. At the moment I'm thinking of playing around with Compiz and its fun 3D bits (in VMWare). However, [http://www.ubuntuforums.org/showthread.php?t=131253](http://www.ubuntuforums.org/showthread.php?t=131253) says that I should have the "fglrx" proprietary video driver-- can I even change that? Is this something as simple as installing "fglrx" from Synaptic/apt-get or a .deb and then switching it over in xorg.conf, or is it essentially impossible for me to run Compiz/xgl on my Mobility Radeon?

Thanks so much. I'll try to contribute back the bits that I know :)

--abk

---

### Post by louis_nichols on 2006-05-09
The fglrx driver is in the repos and can be installed with synaptic. it has a longer name, but I don't remember it right now. Just do a search for the keyword fglrx looking in names only and it will show up.

However, I don't think that will work in vmware, as it emulates a virtual video card of its own...

---

### Post by abk on 2006-05-10
Thanks for the fglrx help-- I installed it through Synaptic just fine. My question now-- how do I tell my system to use it? I learned the hard way that I can't just change the driver name in xorg.conf (fixed easily)-- what do I do now?

---

### Post by louis_nichols on 2006-05-10
well... I was hoping to give you a simple and straightforward answer, but my searches seem to indicate this is not possible. The forum has a different howto for different versions of the driver. I have nvidia, so can't tell you which guide  is better.

I think you should start [here]("http://ubuntuforums.org/showthread.php?t=75378") and [here]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide")

---

