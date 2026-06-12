---
title: "Ubuntu 11.10 not connecting to wi-fi please help Dell XPS M1530"
date: 2011-10-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by LinuxTrix on 2011-10-29
**Ubuntu 11.10 not connecting to wi-fi please help**             
                                                                Hello there,
I decided to upgrade from Ubuntu 11.04 to 11.10, but now when I look in  my network menu in the top right corner, there are no options for  wireless.All that comes up is:

-Wired Network(greyed out)
-VPN Connections
-Enable Networking
-Edit Connections...
P.S. I'm typing this via Ethernet

I'd appreciate it if someone if someone tried to help!
-Sean
                                                                                                   [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]                            [[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=11406378")                                                                                    [[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=11406378")

---

### Post by hansdown on 2011-10-29
Hi, LinuxTrix.

Upgrade, eh?

Are you able, to keep the wired connection, for now, and try the terminal command, that seemed to work in 11.04.

```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
```

---

### Post by LinuxTrix on 2011-10-31
By the way,
for anyone who is having the problem here, I fixed it by activating the Broadcomm STA driver.
Cheers!
-LinuxTrix:popcorn:

---

