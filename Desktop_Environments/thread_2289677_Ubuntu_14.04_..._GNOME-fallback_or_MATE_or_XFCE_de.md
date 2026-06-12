---
title: "Ubuntu 14.04 ... GNOME-fallback or MATE or XFCE desktop Environment"
date: 2015-08-06
forum: Desktop Environments
---

### Post by czgirb on 2015-08-06
in Ubuntu 14.04 ... GNOME-fallback or MATE or XFCE desktop Environment ?
which preferred? which one is faster?

is our system performance will be differ by uninstalling/removing/deleting Unity DE?
by uninstalling/removing/deleting Unity DE will caused our system is unstable ?
if NOT, would you mind to guide me how to remove it?

Please guide me
Thanx

---

### Post by v3.xx on 2015-08-06
They are all slow on a single core processor. but they are all fast on a multi core.  Ram will have a similar effect.  What kind of computer (specs) are you running?

Uninstalling/removing/deleting Unity DE has no performance effect that I am aware of.

---

### Post by czgirb on 2015-08-06
> **v3.xx said:**
> They are all slow on a single core processor. but they are all fast on a multi core.  Ram will have a similar effect.  What kind of computer (specs) are you running?

Uninstalling/removing/deleting Unity DE has no performance effect that I am aware of.

Compaq Presario CQ40 328TU
Intel Core2Duo T6400 2.0-GHz
2 x 1024MB
Intel GMA4500MHD

---

### Post by v3.xx on 2015-08-06
Mate or xfce should run well on those specs, but you may even find a little better performance with lubuntu.

I have ran fallback on a few computers with similar specs and have found it a bit slower than the others.

about your graphics
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Intel+GMA4500&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Intel+GMA4500&sa=Search&cof=FORID:9)

---

### Post by czgirb on 2015-08-06
> **v3.xx said:**
> Mate or xfce should run well on those specs, but you may even find a little better performance with lubuntu.

I have ran fallback on a few computers with similar specs and have found it a bit slower than the others.

about your graphics
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Intel+GMA4500&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Intel+GMA4500&sa=Search&cof=FORID:9)

OK, which one is recommended? MATE or XFCE?
But from your information, I guess Lubuntu DE would be the best. Am I right?
How can I install Lubuntu DE in my system? Is it will make my system unstable?

---

### Post by v3.xx on 2015-08-06
> OK, which one is recommended?
All are recommended :)  I think from there, it a matter of personal choice.  My personal choice was to stay with a flavor that is base in gnome.

There is the option on all installers to try it out before installing.  I would recommend using v14.04; no matter which flavor you choose.  14.04 has long term support (LTS).

---

### Post by v3.xx on 2015-08-06
This may help

[http://www.ubuntu.com/about/about-ubuntu/flavours](http://www.ubuntu.com/about/about-ubuntu/flavours)

---

### Post by deadflowr on 2015-08-06
If you are already running Ubuntu (with unity installed) then I'd suggest installing flashback.
As flashback(fallback/whatever it's called) is better to integrate into the already existing system.
Ubuntu is gnome-based, so you would already have a gnome system in place.

Installing mate or xfce, no matter how slimmed down you try, will bring in extra packages.
Packages built for either the xfce or mate experience.
(You would end up with extra file managers and system settings managers, et cetera et cetera)

as far as unity packages affecting performance, if you don't log into unity, then it's not going to do anything to affect the session you DO log into.

If, however, you would want to do a clean install, either mate or xfce would be fine.
Dealer's choice.

---

### Post by v3.xx on 2015-08-06
> **deadflowr said:**
> If you are already running Ubuntu (with unity installed) then I'd suggest installing flashback.
As flashback(fallback/whatever it's called) is better to integrate into the already existing system.
Ubuntu is gnome-based, so you would already have a gnome system in place.

Installing mate or xfce, no matter how slimmed down you try, will bring in extra packages.
Packages built for either the xfce or mate experience.
(You would end up with extra file managers and system settings managers, et cetera et cetera)

as far as unity packages affecting performance, if you don't log into unity, then it's not going to do anything to affect the session you DO log into.

If, however, you would want to do a clean install, either mate or xfce would be fine.
Dealer's choice.
Yes to that.

Adding Flashback to an existing Ubuntu (Unity) install is very easy.

One line in terminal.
```
sudo apt-get install gnome-panel
```

---

### Post by NathanRodriguez on 2015-08-07
I've tried some of these options and got satisfied with MATE on a 3.0ghz dual core. The option with less memory consumption was LXDE, but I haven't tried Xfce.

---

