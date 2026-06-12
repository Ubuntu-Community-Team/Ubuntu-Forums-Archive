---
title: "Data Acquisition?"
date: 2013-12-16
forum: Education &amp; Science
---

### Post by SwarfEye on 2013-12-16
Hi,

I've got to setup a new data acquisition system for the lab, and I would prefer if possible to use a Linux based solution.

The project is to log 7 differential +-5V signals.

There appears to be a lot of hardware out there that is capable of this, but so far it all the software to run them seems to be Windows.  I've seen a bunch of stuff that claims to have Linux drivers, but I have not yet found a solution that I can see a clear API interface to.  When I get into the documentation on the drivers, everything says something along the lines of "we're working on it, but it doesn't actually work that well"

So the question is...

Is there some sort of Data Acquisition solution out there that works reasonably well with linux out of the box?.. or is this idea really just a massive project in an of itself?

Thanks,

Bill

---

### Post by tgalati4 on 2013-12-16
Describe your use case in a little more detail.  Are you using the data to control a system or are you just data logging for later analysis?

Take a look at Comedi:  [http://www.comedi.org/](http://www.comedi.org/)

---

### Post by morty71 on 2014-01-19
I suggest you use beaglebone or raspberry pi with ubuntu installed on it. You can use the ports for data aquisition if you are familiar with programming...

---

