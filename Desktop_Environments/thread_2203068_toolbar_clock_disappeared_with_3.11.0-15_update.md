---
title: "toolbar clock disappeared with 3.11.0-15 update"
date: 2014-02-01
forum: Desktop Environments
---

### Post by JohnAspinall on 2014-02-01
I'm running an absolutely standard Ubuntu 13.10 install.
Last night, UpdateManager pulled down its regular update; from the log it looks like a new kernel: 3.11.0-15.

After rebooting, nearly everything was fine - unchanged - except that the clock has disappeared from the desktop toolbar.
Furthermore, under settings
(All Settings -> Time and Date -> clock (tab))
all the contents of the clock tab are greyed out (disabled).

Any clues?

---

### Post by howefield on 2014-02-01
Try running the following command in a terminal..

```
killall unity-panel-service
```

---

### Post by JohnAspinall on 2014-02-01
Yes, that worked, thank you!

How about a quick explanation of **why** it worked?  I'm assuming process unity-panel-service was hung, but why would it be hung after freshly rebooting?
And what other process woke up to restore it?  It's running again.

---

### Post by howefield on 2014-02-02
A reboot or logout/in would likely have worked as well.

My understanding is that this bug was fixed with an update, are you fully updated ?

---

### Post by JohnAspinall on 2014-02-02
Yes, I am fully updated.  (Checked by starting Update Manager manually just now.)

I'm still curious as to what other process is restarting unity-panel-service.

---

### Post by leftyleo on 2014-02-15
That command worked for me too ... but my clock was not there from when I first booted

---

