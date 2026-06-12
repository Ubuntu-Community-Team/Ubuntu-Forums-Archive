---
title: "New Libc6 gives me a LOCALE error"
date: 2007-10-17
forum: Desktop Environments
---

### Post by mister_p_1998 on 2007-10-17
Hi guys
I installed a non-standard libc6 (2.6.1.1ubuntu9) in order to get ic2iso working, and Im now getting the error "cannot set locale to " " how do I kill this error or revert to my previous libc6 file? I tried selecting re-install in package-manager, bur its greyed out.

---

### Post by mister_p_1998 on 2007-10-18
Ok Fixed it myself...
entered the following lines

sudo dpkg-reconfigure locales

dpkg-reconfigure localeconf

That went through all the locales entries and allowed me to enter them all as Eng-GB

---

