---
title: "chmsee v1.3.0 Tiny Application Window"
date: 2012-03-03
forum: Desktop Environments
---

### Post by Karlchen on 2012-03-03
Hello, folks.

Since **chmsee v1.0.7** works fine for viewing Windows compiled helpfiles on Lucid Lynx, it seemed to be the best choice for Oneiric Ocelot as well. So **chmsee v1.3.0** got installed on Oneiric.

Yet, **chmsee v1.3.0** exhibits a somewhat weird behaviour:

You launch **chmsee** without passing any arguments to it. It comes up fine. You resize the application window to the size of your choice, use it to view a .CHM helpfile and close it. Next time you launch **chmsee** in the same way it will automatically restore the saved application window size, width and height.

_Now for the strange little nuisance:_

If you pass the name of a .CHM file to chmsee as a commandline argument, i.e. you launch ```
chmsee /path/to/totalcmd.chm
``` e.g. **chmsee** will come up and open the specified helpfile, yet,** it will not restore the saved width and height**. Instead the **chmsee** application window** will have a width of exactly 414 pixels and a height of exactly 195 pixels** (which is really tiny even on a 19" monitor).

The chmsee config file, ~/.config/chmsee/config is owned by me and readable and writable. No access privilege problems involved.

Can anybody reproduce this (minor, but annoying little) problem?
Has anybody got an idea how to work around it? (Except using **xCHM** and except launching chmsee without commandline argument and opening the helpfile afterwards)
Should I file a bug somewhere?

Kind regards,
Karl
--
*P.S.: My current workaround is using xCHM instead of chmsee, because xCHM does not exhibit the reported behaviour.* :wink:

---

### Post by waterloo2005 on 2012-05-11
I find another problem in 1.3.
I can not change font setting in it.
I find every time it starts it will restore its config file ~/.config/chmsee/config to its default.

---

### Post by waterloo2005 on 2012-05-11
I find another problem in 1.3.
I can not change font setting in it.
I find every time it starts it will restore its config file ~/.config/chmsee/config to its default.

---

### Post by waterloo2005 on 2012-05-19
up the thread. Does anyone use chmsee here? Thanks

---

