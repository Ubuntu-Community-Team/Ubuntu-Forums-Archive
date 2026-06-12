---
title: "Using bash to send strings via USB?"
date: 2011-08-17
forum: Education &amp; Science
---

### Post by dumb_question on 2011-08-17
I am cross posting this to the general help forum, not sure about etiquette for that, but anyways...

I am looking to run a couple of pieces of lab equipment from a bash script by sending text commands over USB (specifically a Cheminert switching valve from Vici / Valco and a PHD Ultra syringe pump from Harvard Apparatus). I have both of them working in windows via hyperterminal (after installing drivers). The valve shows up in lsusb without installing a driver (and I can control it via gtkterm) but the pump does not. I know very little about USB protocols - is there a standard way to send text commands over USB, ideally from a bash script?

Thanks!

---

### Post by hubie on 2011-08-22
I don't know exactly how you'd communicate via bash, but you might want to consider throwing something together in python which you can run from bash.  A number of options are listed here:

[http://physics.oregonstate.edu/~hetheriw/whiki/py/sys/21.php](http://physics.oregonstate.edu/~hetheriw/whiki/py/sys/21.php)

---

### Post by dumb_question on 2011-08-23
thanks - I will look into that...

---

