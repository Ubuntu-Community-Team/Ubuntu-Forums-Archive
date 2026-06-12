---
title: "Hydrogen hogs CPU (only in Breezy)"
date: 2005-11-26
forum: Desktop Environments
---

### Post by `GooZ´ on 2005-11-26
I used to use Hydrogen in Hoary with no problems at all, everyting went fine, nice and quick. But in Breezy, when I play my drumloop, it hogs my CPU and it is REALLY slow. I don't know if this is an issue that has to do with the newer version of hydrogen, or with the new kernel, but I guess it's the second, since it runs smoothly in windows.
Could anyone help me with this? Thanks.

---

### Post by yaaarrrgg on 2005-12-20
this thread might help... details three methods for reducing audio latency.

[http://www.ubuntuforums.org/showthread.php?t=97453](http://www.ubuntuforums.org/showthread.php?t=97453)

---

### Post by `GooZ´ on 2005-12-20
Thanks, I will have a look at it now. Other people are still always welcome to post their suggestions here :-)

EDIT: I'm afraid this isn't really what I'm looking for. I don't care that much about the responsiveness of the oudio device in question, I care more about the fact that the GUI takes a lot of time to react. Also, my CPU is really stuck at 100% when I'm using Hydrogen. And I'm a bit afraid to use another kernel, too...

---

### Post by yaaarrrgg on 2005-12-20
If you start hydrogen with a realtime priority, it will fix the sluggish gui too.  I had the same problem.

You don't need to install a different completely different kernel.  You can try set_rtlimits instead (works with the default kernel).  Check out post #18 and #27 in the thread.

---

### Post by `GooZ´ on 2005-12-20
Thx alot! :-) Will try it when I get home! :-)

---

### Post by yaaarrrgg on 2005-12-20
actually, here is a mini howto that is directed more for hydrogen and the sluggish gui problems you're having.  set_rtlimits should fix your problem.

(i've just stripped down the previous howto thread on audio latency)

-----

MY SYSTEM:

I previously added the universe repository to Synaptic Package Manager... and I have previously installed: 

build-essential, linux-headers-2.6.12-9-386, jackd, libjack0.80.0-dev, qjackctl, and hydrogen

Also, not sure if it matters, but  I configured Breezy to use "alsa" for input and output. In Gnome, this is set at: System -> Preferences -> Multimedia Systems Selector

-----

HOWTO SETUP RTLIMITS (FOR BREEZY DEFAULT KERNEL)

```

#switching to superuser... working in tmp directory
sudo -i
cd /tmp

#get and unpack set_rtlimits program
wget http://www.physics.adelaide.edu.au/~jwoithe/set_rtlimits-1.1.0.tgz
tar xvzf set_rtlimits-1.1.0.tgz
cd set_rtlimits-1.1.0

# this should compile the program and install
# note though... 
# i've already installed linux-headers and build-essential with apt-get
make
make install

```

For me, this compiled and installed on Breezy without any errors.  To configure it now, you'll need to add the programs you'll invoke in the config file /etc/set_rtlimits.conf

For me, the file looks like this (my username is kevins)
```

# Configuration file for set_rtlimits.  Format is:
#
#   username   program   max_nice_priority  max_realtime_priority

kevins  /usr/bin/jackd  -1  100
kevins  /usr/bin/hydrogen -1  100

```

Now you are ready to go.  I wrote a quick script to launch jackd and hydrogen, (although there are probably countless better ways to do this).

```

#!/bin/bash

# start a clean instance of jack
killall jackd
set_rtlimits -r=30 /usr/bin/jackd -R -d alsa -d hw -r 44100 -p 256 -n 2 &

# start hydrogen
sleep 1
set_rtlimits -r=30 /usr/bin/hydrogen

# clean up
killall jackd

```

without doing this, hydrogen was just too sluggish to be useful.  You may need to experiment with the priorities though.  Setting the priority too high will cause the gui to be slugish again.

---

### Post by willistg on 2005-12-24
i just noticed this sluggishness as well.

A temporary fix it seems would be to close the song editor window, that seems to be the guy that's hogging things. Though I would have expected the mixer window with it's n # of traks/levels would have been it.


It's just weird. I wish I could install the .92 official release rather than the beta.

---

