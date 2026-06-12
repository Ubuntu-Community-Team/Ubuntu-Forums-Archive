---
title: "Sound card not found"
date: 2006-06-02
forum: Desktop Environments
---

### Post by tavito on 2006-06-02
Hi Ubuntu fans!

i've just updated my fully functional Breezy to Dapper, and after rebooting i've obteined the following issues:

- I have to reconfigure my eagle-usb modem each time I boot (doing 'sudo eagleconfig'), because the kernel module is not recognized at boot time.

- The sound doesn't work. If I launch KInfoCenter I can see that there's no Sound card recognized, and exactly the same I obtein after doing 'sudo /etc/init.d/alsa-utils start':

* Setting up ALSA...                                                                                                                          * warning: 'alsactl restore' failed with error message 'alsactl: load_st[ ok ]36: No soundcards found...'...

Do you think both troubles are related? Maybe there's some problem with the kernel modules...

Some clue to solve them?

Thanks in advance ;-)

---

