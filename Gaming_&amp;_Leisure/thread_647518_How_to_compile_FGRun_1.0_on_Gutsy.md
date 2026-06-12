---
title: "How to compile FGRun 1.0 on Gutsy"
date: 2007-12-22
forum: Gaming &amp; Leisure
---

### Post by solbot on 2007-12-22
After **much** searching and messing around I finally managed to compile fgrun 1.0.0 on Gutsy.

Here's How.

_Setup_
You need several things to make this work.
The list of required packages are:
[LIST]
[*]libopenal0a
[*]libopenal-dev
[*]libalut0
[*]libalut-dev
[*]plib1.8.4c2
[*]plib1.8.4-dev
[*]zlib1g
[*]zlib1g-dev
[/LIST]

You can use either apt-get or synaptic to install these.

Download the source for both simgear and fgrun.
Simgear: [http://www.simgear.org/]("http://www.simgear.org/")
Fgrun: [http://sourceforge.net/projects/fgrun]("http://sourceforge.net/projects/fgrun")

Extract both to a directory.

Open a console and go to the simgear directory first.

Run
 ```
./configure --prefix=/usr/ --with-jpeg-factory
```
Then
```
make
```
Then either run checkinstall or ```
sudo make install
```

Finally, enter the Fgrun directory and run ```
make; sudo make install
```

Anything I've missed? Let me know so I can fix it.

Can't compile it?
Get my Debs from [here]("http://fiddler.homeip.net/debs")

Merry Christmas.

---

### Post by FokkerCharlie on 2008-01-20
Hi solbot

Thanks for the instructions.  I followed them, and SimGear and FlightGear seemed to compile OK.  However, when I try to run (typing fgfs in the terminal), I see the following message:

/usr/share/FlightGear-1.0.0

Base package check failed ... Found version [old version] at: /usr/local/share/FlightGear
Please upgrade to version: 1.0.0


It is version 1.0.0 there- promise!

Any ideas?

Charlie

---

### Post by solbot on 2008-01-21
No idea unfortunately. I compiled fgrun against simgear, but haven't tried compiling flightgear yet.

If you use the version of flightgear that is in the repository, then my instructions should work.

You could check that the synaptic version of flightgear is completely uninstalled before compiling your own version 1.0.0, but as I said this tutorial was for fgrun so I'm not sure.

---

### Post by viciouslime on 2008-01-21
You need to make sure you extract the new base package to "/usr/local/share/FlightGear". You should NOT have the version of flightgear from the repos installed.

---

### Post by FokkerCharlie on 2008-01-21
Ah!

The base package thingie fixed it.

Thanks!

Charlie

---

### Post by Darganot on 2008-01-24
The .deb works like a charm, thanks!  Just having trouble connecting to the multiplay from behind my firewall.

---

### Post by feranick on 2008-01-27
Other debs available here:

[http://www.getdeb.net/release.php?id=2029](http://www.getdeb.net/release.php?id=2029)

---

### Post by insomniux on 2008-06-07
Hi,
also needed to install libfltk-dev to make it to compile. fgrun now works perfect again! 
Thanks
insomniux

---

### Post by jjchico on 2008-07-12
I managed to compile fgrun 1.0.1 in hardy without compiling flightgear or extra libraries. I have written a Howto:

[https://wiki.ubuntu.com/JorgeJuan/FgRunHowTo](https://wiki.ubuntu.com/JorgeJuan/FgRunHowTo)

Comments are welcome.

Enjoy!

---

