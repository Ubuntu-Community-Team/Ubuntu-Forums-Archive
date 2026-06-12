---
title: "PyKDE installation problem..."
date: 2005-04-23
forum: Desktop Environments
---

### Post by J-Doe on 2005-04-23
Okay, I'm trying to install PyKDE because [Slickbar](http://www.unrandom.com/Projects/slickbar.php) requires it...

I got following error:
> d@dpc:~ $ sudo apt-get install python-kde3 -f
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  python-kde3: Depends: python (< 2.4) but 2.4.1-0ubuntu2 is to be installed
               Depends: python2.3-kde3 but it is not going to be installed
E: Broken packages 

So I checked Synaptic and it claims that I have both Python 2.3 and 2.4 installed.
What can I do? :)

---

