---
title: "Dell Latitude D600 - No Network Connections"
date: 2013-07-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cessanfrancisco on 2013-07-13
My office was throwing out some old computers and I was able to save an old Dell Latitude D600.

When I tried to install Ubuntu on it, it didn't seem to like it (something about PAE).  So I installed Ubuntu 9.10 which seems to run very well.  One problem:  when I was running it live the network connections worked fine.  I was able to use my WiFi signal.  Once installed even though it says the networks card and WiFi adapter are both enabled I cannot connect either through the ethernet or the WiFi.  I tried connecting through the live USB, as before, and this won't work now.

Any suggestions on how to get the network connections working?

Thanks in advance.

---

### Post by TheFu on 2013-07-13
9.10 has been unsupported - i.e. no patches for 3 years!!!!  PAE kernels became the Ubuntu default around 12.04, I think.  Hopefully, someone else here will post the exact time, so you will not be able to use any default Ubuntu desktop install that is currently supported with the PentiumM CPU in that machine.  I had both a D600 and 600M laptop - **I miss the 1440p screens on both!**

My suggestion would be to switch to a different, currently supported, non-PAE, distro.  Debian desktop would be the most similar.  I don't know if Ubuntu's Alternate install has non-PAE kernels, but that could be a choice too - Mint follows Ubuntu.  Debian is probably the best answer today, unless you are willing to leave APT. ;(

**Under no situation should you put a non-supported Linux OS on the internet.**

---

### Post by Cheesemill on 2013-07-13
You can use the non-PAE version of the 12.04 mini CD to install from.
[http://cdimage.ubuntu.com/netboot/precise/](http://cdimage.ubuntu.com/netboot/precise/)

Ubuntu 12.04 is supported until 2017.

---

### Post by TheFu on 2013-07-13
THANKS @Cheesemill.  I'm organizing an InstallFest in August at our LUG and that information will be critical for our success.

---

### Post by cessanfrancisco on 2013-07-13
Thanks for your input everyone.  It's greatly appreciated.

However, I have managed to get 9.04 installed.  It's just the networking and wifi aren't working despite the fact that they are "enabled."  Everything else works fine.  Do you think it might just be a driver issue?

---

### Post by TheFu on 2013-07-13
> **cessanfrancisco said:**
> Thanks for your input everyone.  It's greatly appreciated.

However, I have managed to get 9.04 installed.  It's just the networking and wifi aren't working despite the fact that they are "enabled."  Everything else works fine.  Do you think it might just be a driver issue?

Running 9.04 is like running Windows95, except the release isn't so old that it can't be hacked.  We're really trying to get you to a currently supported release where any bugs might be fixed by the developers.

The problem could be anything. driver, hardware, GUI management tool.  I'd love more facts and data, but can't tell you exactly where and what to type since I haven't used 9.04 in about 4 yrs.  I'm really very sorry that I can't help more in the way you want.

---

### Post by cessanfrancisco on 2013-07-14
Thanks for your help.

I'll probably look into installing the non-PAE version.

---

### Post by mörgæs on 2013-07-15
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

Bodhi Linux is another option. Support for non-PAE processors through 2017.

---

