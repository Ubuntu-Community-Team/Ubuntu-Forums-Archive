---
title: "when &quot;sudo gedit&quot; command does not run..."
date: 2005-12-02
forum: Desktop Environments
---

### Post by yioan on 2005-12-02
I have seen many posts relating to this, that the sudo gedit does not run. In my computer the problem was that the loopback adapter was down.

Check  if the loopback adapter is up.

When pppoeconf is used for configuring a pppoe connection, it puts a line in the /etc/network/interfaces and following that the ifup used at the boot up to turn on the loopback adapter does not work properly. When loopback adapter is down you have some problems like:
     - sudo gedit can not run
     - disk-admin tools run after 3 minutes in a p4
     - lags in many gnome tools


the solution is to
execute the "sudo ifconfig lo up" command each time you start ubuntu
or edit the interfaces file and remove the line that pppoeconf has inserted. (there is a note next to this line, usually it is the last one) and run the "sudo ifup -a" or restart ubuntu

this was the issue in my computer...

---

### Post by polpak on 2005-12-02
You should submit this to bugzilla

---

### Post by aysiu on 2005-12-02
[https://bugzilla.ubuntu.com/](https://bugzilla.ubuntu.com/)

In the meantime, ```
sudo nano
``` is a great alternative.

---

