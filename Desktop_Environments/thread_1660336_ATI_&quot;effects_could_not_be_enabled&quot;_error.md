---
title: "ATI &quot;effects could not be enabled&quot; error"
date: 2011-01-05
forum: Desktop Environments
---

### Post by swatsbiz on 2011-01-05
Struggled with this since adding a dodgy apt source for ati drivers.  I have tried to revert my drivers to the previous settings but desktop effects still won't enable :-(

Normally I'd just do a fresh install, but I feel I should dig a bit this time.

Many thanks in advance

---

### Post by realzippy on 2011-01-05
Which driver/repo ?
Which graphics card?

---

### Post by swatsbiz on 2011-01-05
> **realzippy said:**
> Which driver/repo ?
Which graphics card?

Graphics Card is: ATI Radeon HD 5450

Driver is 8.723.1-100408a-098580C-ATI

Repo currently used is: [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu)


And for Compiz it's: [http://ppa.launchpad.net/compiz/ppa/ubuntu](http://ppa.launchpad.net/compiz/ppa/ubuntu)

---

### Post by realzippy on 2011-01-05
So you have removed those PPAs correctly?
ppa-purge ?(eg: [http://bigbrovar.aoizora.org/index.php/2010/01/10/how-to-safely-remove-ppa-repository-from-ubuntu/](http://bigbrovar.aoizora.org/index.php/2010/01/10/how-to-safely-remove-ppa-repository-from-ubuntu/))

---

### Post by swatsbiz on 2011-01-05
Thanks, that finally sorted it, although I'm sure I had purged them previously ...

Purged both the x ppa and the compiz one, deactivated the video driver, from additional drivers, and rebooted. Then re-activated the video driver.

Thanks!

---

### Post by realzippy on 2011-01-06
Fine;so can you set thread as "solved" (Threadtools)?

---

