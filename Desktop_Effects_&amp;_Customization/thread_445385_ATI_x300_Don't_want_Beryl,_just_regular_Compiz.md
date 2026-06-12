---
title: "ATI x300: Don't want Beryl, just regular Compiz"
date: 2007-05-15
forum: Desktop Effects &amp; Customization
---

### Post by Neuralgia on 2007-05-15
Feisty 7.04
ATI x300

I don't want beryl, just regular cube and wobbling windows... other stuff too much for me

After I install the restricted drivers, those are gone.

Is tere a way to have them w/ this card, and the restricted drivers? or the only way is the uninstall it .

thanks

---

### Post by RAOF on 2007-05-15
Since the proprietary drivers don't support all the necessary extensions for Compiz & Beryl (namely, Composite (aka: transparency) + GL), you need to use [XGL](wiki.ubuntu.com/CompositeManager/Xgl).  Set up XGL as in the link, and Compiz (but not Beryl, because beryl-xgl isn't built in the Feisty package) will work.

Alternatively, you could **uninstall** (not simply disable) the proprietary fglrx drivers.

---

### Post by Neuralgia on 2007-05-18
thanks... making an XGL session worked like a charm

---

### Post by Bohlio on 2007-05-18
I have a few quick questions and if they seem rediculous to you, please take into acount that this is about my third day on Ubuntu, Ive never dealt with Linux before. :-)

Is the proprietary fglrx driver the one available in the restricted drivers manager?
What is Compiz? Is it the desktop effects that come installed with Ubuntu 7.04?
Are there any negatives at all to using XGL? and what is the alternative to XGL that is used in a default install of 7.04?

Thank you :-)

---

