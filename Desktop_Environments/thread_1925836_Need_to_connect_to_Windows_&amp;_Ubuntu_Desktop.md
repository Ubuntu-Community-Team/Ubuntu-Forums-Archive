---
title: "Need to connect to Windows &amp; Ubuntu Desktop"
date: 2012-02-15
forum: Desktop Environments
---

### Post by moe19790 on 2012-02-15
Hi,

I do need the equivalent programs in Lubuntu to

1- remote desktop view
2- terminal server client

i was using those progs in ubuntu to connect to other machines but now i`m using Lubuntu and i can`t find the equivalent.

Thanks

MOe!

---

### Post by aeiah on 2012-02-15
the program is called tsclient
```

sudo apt-get install tsclient
```

---

### Post by moe19790 on 2012-02-15
hi,

i was expecting tsclient to be a gnome based app! Does it work on LXD? since i want to use it with Lubuntu Not Ubuntu.. Please advice.

Thanks

MOe!

---

### Post by kc1di on 2012-02-15
> **moe19790 said:**
> hi,

i was expecting tsclient to be a gnome based app! Does it work on LXD? since i want to use it with Lubuntu Not Ubuntu.. Please advice.

Thanks

MOe!

LXDE uses GTK Libs so it will work with most gnome programs.

---

### Post by moe19790 on 2012-02-15
> **kc1di said:**
> LXDE uses GTK Libs so it will work with most gnome programs.


Thank you for the info :)

MOe!

---

### Post by aeiah on 2012-02-15
yea, some gtk based apps could be considered gnome apps in that they require one or more gnome libraries. you'll be able to see when installing things through apt-get, aptitude or synaptic what dependencies are required. i usually try not to install things if it lists a load of gnome dependencies, but there's no harm in doing so really.

tsclient uses gtk (like openbox, what lxde/lubuntu uses) but no gnome libraries as far as i know.

even some apps that sound like they should be gnome-dependant don't use any gnome libraries, like GMPC (gnome media player client) and backintime-gnome (which just uses gtk as far as i know). its worth noting too that some apps that begin with a 'g' might have nothing to do with gnome, such as gimp (gnu image manipulation program).

---

