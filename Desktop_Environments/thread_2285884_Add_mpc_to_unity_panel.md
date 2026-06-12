---
title: "Add mpc to unity panel"
date: 2015-07-08
forum: Desktop Environments
---

### Post by chris137 on 2015-07-08
Hey,
I am controlling a remote MPD-server with mpc on my ubuntu-machine.
I'd like to add that info as indicator to my unity panel.
Is there a way to do this?
Simple commands like volume and next track would be alright.
Ideally it would be inside the existing sound indicator.
I couldn't find where the config is stored for that.

Thanks

---

### Post by mc4man on 2015-07-09
The existing sound indicator would require mpris2 support, can you make use of mpdris2

---

### Post by chris137 on 2015-07-09
That looks like it's supposed to do exactly what I want!
Sadly I could not test it yet because I can't install it. Issue has been opened at github.
Maybe you want to take a look: [https://github.com/eonpatapon/mpDris2/issues/67](https://github.com/eonpatapon/mpDris2/issues/67)

If that gets resolved I guess I'll be happy.

---

### Post by mc4man on 2015-07-09
As it happens I had a new 14.04.3 install in place with absolutely no build packages installed. So installed these & ran the autogen.sh from the downloaded master (zip), went fine
So run this single command, see if anything gets installed - 
```
sudo apt-get install autoconf automake autopoint autotools-dev build-essential \
dpkg-dev g++ g++-4.8 intltool libstdc++-4.8-dev libtool
```

Or alternately run sudo apt-get build-dep mpdris2 
(- though that will also install some packaging packages..

---

### Post by chris137 on 2015-07-10
Thanks, that did work!
After I also had to install python-mpd to run it I am now 100% happy.
Well.. Make it 98. Sound-control and covers from spotify would be nice too, but I'll look into that another time.
For now this is solved, thanks again.

---

