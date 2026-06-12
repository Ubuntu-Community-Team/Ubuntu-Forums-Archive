---
title: "Synaptic missing after update to Hoary"
date: 2005-03-29
forum: Desktop Environments
---

### Post by BarbiGirl8 on 2005-03-29
I just updated to Hoary tonight and everything seems to be fine, but for some reason I've totally lost Synaptic. I can apt-get but I don't have the Synaptic GUI in any of my menus. This doesn't make any sense :sad: Any help would be appreciated.

---

### Post by BarbiGirl8 on 2005-03-29
Ok, I tried to apt-get synaptic and got the following:

```
$ sudo apt-get install synaptic
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
  synaptic: Depends: libapt-pkg-libc6.3-5-3.3
E: Broken packages

```

Then I did the following and here are the results

```

 $ sudo apt-get install libapt-pkg-libc6.3-5-3.3
Reading package lists... Done
Building dependency tree... Done
Note, selecting apt instead of libapt-pkg-libc6.3-5-3.3
apt is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

---

### Post by BarbiGirl8 on 2005-03-29
Ok, I figured it out. I went into my source.list and commented out everything but the hoary source's and then re-ran the 

```

sudo apt-get install synaptic

```

And it Worked!!! I'm so happy I could do a dance. Well actually I did do a dance. Maybee this will help someone else with this problem.

---

### Post by jMack on 2005-03-31
Dude!

I did a little dance-of-thanks in my office here.
(good thing nobody was looking...I'm terrible)

Great work! Exactly what I needed.

---

### Post by regshoe on 2005-10-04
And so did I ;)

Thx for your help!

---

