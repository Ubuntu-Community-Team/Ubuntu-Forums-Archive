---
title: "Mouse"
date: 2005-10-04
forum: Desktop Environments
---

### Post by seismicmike on 2005-10-04
Hey, does anybody know how to toggle my notebook's built in mouse on/off???

---

### Post by KingBahamut on 2005-10-04
Mike, you could try to disable it the BIOS. 
What laptop model and manufacture?

---

### Post by brentoboy on 2005-10-04
if your touchpad is a synaptics touchpad, maybe qsynaptics will help.

---

### Post by seismicmike on 2005-10-05
hmm... apt-get won't let me download qsynaptics :(

```

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
  qsynaptics: Depends: xfree86-driver-synaptics but it is not going to be installed
E: Broken packages

```

my laptop is a Gateway m320, and I could do it in BIOS, but there are times when I do want to be able to use it... right now I have about 10 sheets of paper duct taped over it, and that's more convenient than bios, b/c I can always pry those off... it'd be nice if I could just toggle it on and off, like I do/did in Windows.

---

### Post by seismicmike on 2005-10-05
this is what I get when I try to apt-get that xfree86-synaptics:

```

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
  xfree86-driver-synaptics: Depends: xserver-xfree86 (> 4.1.0)
E: Broken packages

```

Suggestions??

---

