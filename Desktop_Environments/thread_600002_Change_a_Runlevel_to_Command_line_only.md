---
title: "Change a Runlevel to Command line only"
date: 2007-11-01
forum: Desktop Environments
---

### Post by isolve on 2007-11-01
May I know how do I configure a runlevel to run minimal process in command line.  A I need is networking and SSH server.  I still want to boot into the default GUI, but sometimes I would like to switch to Command line with minimal process running.

Thanks.

---

### Post by taurus on 2007-11-01
You can kill gdm or remove it.  And if you want to get into Gnome, just run **startx** at the prompt.

---

### Post by john lejeune on 2007-11-02
Since Feisty, Upstart replaces the init daemon.

You can take a look at **/etc/event.d/** and write your own jobs thanks to [http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html)

---

