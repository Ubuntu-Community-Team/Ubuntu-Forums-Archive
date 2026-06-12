---
title: "Adventures while trying to install XConq"
date: 2015-08-23
forum: Gaming &amp; Leisure
---

### Post by Talorgan on 2015-08-23
It looks good [https://www.sourceware.org/xconq/](https://www.sourceware.org/xconq/) but it's not in the Software Centre.

The instructions within the downloads from the above site are in Double Dutch (apologies to Linux old hands for that comment) although they do say "both the tcl and tk libraries must be already built and available. Many recent systems, such as Linux, have tcl/ tk preinstalled, and you can just use those."

Next, I found and downloaded:

xconq-doc_7.4.1-4.1ubuntu1_all.deb

xconq-common_7.4.1-4.1ubuntu1_all.deb

xconq_7.4.1-4.1ubuntu1_amd64.deb

Right-clicking the first two allowed me to go to the Software Centre and apparently install them. Attempting the same trick with the third brings up the message "Dependency is not satisfiable: tcl8.3 (>=8.3.5)".

There is already a "Tool Command Language" on the computer, specifically "tcl 8.6.0+6ubuntu3". (The machine I have is running 14.10)

I reckon that if I removed this and replaced it with 8.3 the game might work but the computer might not. That in turn would mean that the game is not compatible with the latest versions on *buntu. That would mean that if I want to discover the joys of XConq I'll have to dig out my old Windows XP box, which is sitting looking forlorn, disconnected and gathering dust in the corner.

Whadaya reckon?

---

### Post by ian-weisser on 2015-08-24
Xconq package used to be available for Debian and Ubuntu. I played it, too.
It was dropped a few years ago when the upstream withered. An actively maintained upstream is a minimum requirement.

Each package in a version of Ubuntu needs to use that version's dependencies.
That's one purpose of a distro - all software uses the same dependencies, including the same versions. It avoids many Windows DLL problems, and keeps software much smaller.
You are trying to install an older deb for a previous version of Ubuntu, with older dependency requirements. Sometimes it works, sometimes it doesn't.

You are trying to install a package on a system it is not intended for. Failure is the expected result. There is no easy way to work around that.

There are, however, non-package solutions: You can compile and install Xconq from source. That will always work, though it does require knowledge of how to compile.

---

### Post by Talorgan on 2015-08-24
Thank you for your response and the explanation, which makes a lot of sense.

There is nothing else for it, I will have to learn to compile. Since I have been using Linux for years now it's high time I did.

One question though: what is an "upstream"? Is it human demand?

---

### Post by ian-weisser on 2015-08-24
Upstream projects create and maintain source code. The code flows downstream to distros like Debian, then to Ubuntu, and finally to you.

'Upstream' in this context means the (moribund) organization that created and maintained the Xconq source.

---

### Post by Talorgan on 2015-08-25
Thanks again

... and Cheers!

---

### Post by Feneric on 2015-09-06
I made some minor adjustments to it that enable it to build & install on modern Ubuntu. You can find my changes here:

[https://github.com/Feneric/xconq](https://github.com/Feneric/xconq)

Hope this helps.

---

### Post by Talorgan on 2015-09-06
I'll give it a whirl. Thanks.

---

### Post by Feneric on 2015-09-07
You're welcome. It's not a package, but it should build and install pretty readily and I've played through a complete game with it. Please let me know if you have any problems.

---

### Post by Talorgan on 2016-01-19
Sorry it has taken me so long to reply to you but unfortunately I am no further forward. Tcl remains the issue. The version required by the game is different from that on the computer.

---

### Post by sefufuller on 2016-10-29
Thank you Feneric for keeping the xconq package alive.
the source package from [https://github.com/Feneric/xconq](https://github.com/Feneric/xconq) works well.

on 16.04 LTS in order to install xconq i did the following:

```
sudo apt-get install tcl8.6-dev tk8.6-dev libxmu-dev libxaw7-dev
./configure
sudo make install

```

---

### Post by Talorgan on 2017-03-07
Made it to the last line:

talorgan@Hans:~/the folder I was using/xconq-master$ sudo make install
make[1]: Entering directory '/home/talorgan/the folder I was using/xconq-master/tcltk'
Makefile:347: *** missing separator (did you mean TAB instead of 8 spaces?). Stop.
make[1]: Leaving directory '/home/talorgan/the folder I was using/xconq-master/tcltk'
Makefile:140: recipe for target 'all-tcltk' failed
make: *** [all-tcltk] Error 2

---

