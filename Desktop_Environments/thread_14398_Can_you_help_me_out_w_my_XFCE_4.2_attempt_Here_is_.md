---
title: "Can you help me out w/ my XFCE 4.2 attempt? Here is the install log..."
date: 2005-02-07
forum: Desktop Environments
---

### Post by spaceballl on 2005-02-07
I definitely know that i'm not alone in the pool of Ubuntu users having a pretty tough time getting XFCE 4.2 up and running. Just some background on what I did...

I downloaded the most recent Hoary build ISO that I could find (i tried this with warty so I thought going to hoary might help). Immediately after install, i got all the dependency files that the XFCE installer says you need. Ran the installer. Got into the GUI for it and everything and around 5%, it craps out...

It aborts install when it is in the XFCE Utility Library section. I get "Running configure... failed". I click "error log" and i get the following (i'm only pasting the last few lines or so)...

"
checking how to recognise dependent libraries... pass_all
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
!! Failed to configure libxfce4util, see the errors above
!! for details on the problem.
"

So something wrong w/ my C++?? I just don't get it. Please help me out if you can!

-Kevin

---

### Post by spaceballl on 2005-02-07
Ugh as much as I have enjoyed coming to Ubuntu from Fedora... Fedora was better w/ XFCE... very simple.

---

### Post by spaceballl on 2005-02-07
Okay so for those who may be having similar problems... The problem was another dependency issue that the installer didn't pick up on. Go to Synaptic and search for G++, C++, and CPP. Get all of those packages... The weird thing is that I thought having the newest version of everything was the best. Install the older versions too though because I think the XFCE defaults to those instead and won't work with the new ones.

So now I can get like 60% into the install, and it crashes. This time I can't get a good enough description to figure out what went wrong so I went in to Synaptic and I dunno... i got more packages, but I'm not sure what I just got. I grabbed anything that looked compiler-ish. I CAN tell you that it crashed during the "make" process of XFCE-Session... anyone have advice?

---

### Post by az on 2005-02-07
Are you installing from a tarball?  What does it say it needs to compile in the README?

Go and install those packages.  Get build-essential and any -dev packages that it needs (x library development files are name xlibs-dev, for example)

And use Warty.  Do not be surprised if Hoary borks out at this stage...

---

### Post by valadil on 2005-02-07
This probably isn't the answer you're looking for, but there are ubuntu compatible repositories with xfce4.2 out there.

Just add the following lines to your /etc/apt/sources.list:
deb [http://www.os-works.com/debian](http://www.os-works.com/debian) testing main
deb-src [http://www.os-works.com/debian](http://www.os-works.com/debian) testing main

Or these if you're on amd64:
deb-src [http://www.os-cillation.de/debian](http://www.os-cillation.de/debian) source/
deb [http://www.it-weber.net/debian/xfce4/](http://www.it-weber.net/debian/xfce4/) ./

apt-get update, then grab xfld-desktop from apt.  You might have to force a couple packages through (pump, for instance) and apt will bitch that your sources aren't verified, but these repositories will work.

---

