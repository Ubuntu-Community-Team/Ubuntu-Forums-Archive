---
title: "Broken Ruby Package"
date: 2009-01-19
forum: General Help
---

### Post by tizzod on 2009-01-19
I just downloaded Ubuntu 8.1 Server edition as I want to set up a ROR hosting box.

I tried installing ruby and a few other packages, but had broken dependencies.  i installed ruby fine, here's my dpkg:
```
ii  libruby1.8                        1.8.7.72-1                    Libraries necessary to run Ruby 1.8
ii  ruby                              4.2                           An interpreter of object-oriented scripting 
ii  ruby1.8                           1.8.7.72-1                    Interpreter of object-oriented scripting lan
```

but when I got to install irb and ri I get this:

```
sudo apt-get install irb1.8 ri1.8
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  irb1.8: Depends: ruby1.8 (>= 1.8.7.72-1ubuntu0.1) but 1.8.7.72-1 is to be installed
  ri1.8: Depends: rdoc1.8 (= 1.8.7.72-1ubuntu0.1) but it is not going to be installed
E: Broken packages

```

Is this really a bug?

---

### Post by tizzod on 2009-01-19
So i was digging around the repo's and noticed that there's ruby1.8.7.72-1 and ruby1.8.7.72-1ubuntu0.1 packages.  I Don't know what the difference is, but it appears that when I go to install irb1.8, it's dependent on the latter package, when in fact, apt installed the former.  I manually downloaded the irb1.8_1.8.7.72-1_all.deb instead of the irb1.8_1.8.7.72-1ubuntu0.1_all.deb and installed it using gdebi.  

Can someone tell me exactly what's gone on here?  Why are there discrepancies between the packages apt is installing, if I want the ubuntu packages, why did apt install the "normal" ruby package in the first place.  I guess I can do the same thing now for ri1.8.  My only concern is that gdebi finds all dependencies and installs them, so my libreadline-ruby1.8 is 1.8.7.72-1ubuntu0.1 whereas all the other ruby packages are just 1.8.7.72-1.  Is this a concern?

---

