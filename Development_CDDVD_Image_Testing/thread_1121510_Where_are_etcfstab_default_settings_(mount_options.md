---
title: "Where are /etc/fstab default settings (mount options) stored?"
date: 2009-04-10
forum: Development CD/DVD Image Testing
---

### Post by wolfchri on 2009-04-10
Hello there,

for a customized edition (remastersys) of the upcoming Ubuntu 9.04, I want to change the default mount options for ext3/4 (currently defaults,relatime).

However, I do not find the place where they are stored - I guess that they are buried somewhere in ubiquity or casper. but where?

Any hint would be helpful.

Thank you a lot!

---

### Post by wolfchri on 2009-04-10
Solved it myself:

The default filesystem settings / mountoptions are in 

/lib/partman/mountoptions

Hat tip to myself ;-)

---

