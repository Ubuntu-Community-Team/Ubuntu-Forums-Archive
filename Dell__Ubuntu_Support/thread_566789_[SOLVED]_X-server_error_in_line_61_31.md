---
title: "[SOLVED] X-server error in line 61 31"
date: 2007-10-03
forum: Dell  Ubuntu Support
---

### Post by blandonfrank on 2007-10-03
Hi,

First of all I would like to say that this is a great forum. 

I'm extremely new to Linux, started with Ubuntu 7.04 and I installed a Dell 1390 wireless card. However, in the process of doing it, I misspelled something on a line of code and now the X-server doesn't want to boot in a graphical way.

This is exactly what it says when I boot up my system.:

```
Warning : /etc/modprobe.d/blacklist line 31 : ignoring bad line starting with 'blcklist'
```


kinit: name_to_dev_t (/dev/disk/by-uu id/5a14f95c-31fc-41e7-95rf-40c4f89a96d3) = sda5 (8,5)

Can someone please assist me. 
Please note that the misspelled was : blcklist when I was trying to write blacklist. Now, how can I fix this.

Thanks in advance/

---

### Post by ImNeat on 2007-10-04
After xserver fails you'll be brought to the shell. Log in as your user and open the configuration file with nano as administrator:

'sudo nano /etc/modprobe.d/blacklist'

find and correct your error. save changes with 'ctrl-o, enter' and exit with 'ctrl-x' then reload your gui with 'startx'

---

### Post by blandonfrank on 2007-10-04
Problem solved. Thanks!

Apparently, there was also a problem with Nvidia driver. I installed it with Envy and for some reason I kept getting an error. I re-installed it with Envy and now its working fine.

Thanks for the help.

---

