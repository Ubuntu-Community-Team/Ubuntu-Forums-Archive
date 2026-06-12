---
title: "Evince not working"
date: 2010-11-15
forum: Desktop Environments
---

### Post by GnuBoi on 2010-11-15
Guys,
I did following to update my evince in ubuntu 10.04:
> sudo apt-get install evince
and once the evince was updated now, it doesn't work.
When I type evince in terminal it says following:
> evince: symbol lookup error: evince: undefined symbol: ev_get_locale_dir


So, googled the problem and found some solved ubuntu threads but that didn't work for me. Like 
sudo apt-get install libevdocument2
sudo apt-get install libevview2

Reinstall also brings same problem:
 1428  sudo aptitude --reinstall evince
 1429  sudo aptitude install evince
 1430  sudo aptitude install update
 1431  sudo aptitude update
 1432  sudo aptitude remove evince
 1433  sudo aptitude install evince ubuntu-desktop 

Nothing works! 
Evince is one of the important component of my desktop. Please any help ? 
Thanks in Advance.

---

### Post by Ophidion on 2011-04-11
Hi,
    I had the same problem like yours and it was solved by installing:
sudo apt-get install libevdocument2

anyway save these lines to atext file open synaptic and load markings it may help:

evince        install
libevview2        install
libevdocument2        install
libpoppler5        install
libpoppler-glib4        install

hope it works. thanks.

---

