---
title: "Where is Wvdial.conf in ubuntu 9.04??"
date: 2009-04-29
forum: General Help
---

### Post by mahenkpatel on 2009-04-29
Just installed ubuntu 9.04 in my laptop.

Earlier i used to connect to internet through wvdial, but in 9.04 i cant find wvdial.conf in filesystem>>etc folder where it was in 8.10.

Do i need to install it separately?? If yes how can i do this with the help of ubuntu 9.04 desktop cd because i cannot connect to internet.

Please help its urgent!!

Thanks

---

### Post by kpkeerthi on 2009-04-29
I found some intructions on how to get this file generated here: [http://en.wikipedia.org/wiki/Wvdial]("http://en.wikipedia.org/wiki/Wvdial")
You may have to use sudo while running those command. I have personally not used this tool so I'm not very sure.

---

### Post by evilaim on 2009-04-29
locate wvdial.conf

or 

sudo apt-get install wvdial

---

### Post by LowSky on 2009-04-29
Well your on the internet somehow? Hopefully you have a flash drive or someway to copy this file im giving you in a link.
[http://freshmeat.net/urls/0d99966dedee7b9f2b0a92fcb84e7a6c](http://freshmeat.net/urls/0d99966dedee7b9f2b0a92fcb84e7a6c)

Just so you know wvdial isn't included like it was before, supposedly its been replaced.

---

### Post by mahenkpatel on 2009-04-29
> **LowSky said:**
> Well your on the internet somehow? Hopefully you have a flash drive or someway to copy this file im giving you in a link.
[http://freshmeat.net/urls/0d99966dedee7b9f2b0a92fcb84e7a6c](http://freshmeat.net/urls/0d99966dedee7b9f2b0a92fcb84e7a6c)

Just so you know wvdial isn't included like it was before, supposedly its been replaced.

Its .tar.gz file, i dont know how to install it, can you give some link to .deb file.

Thanks

---

### Post by mahenkpatel on 2009-04-29
> **evilaim said:**
> locate wvdial.conf

or 

sudo apt-get install wvdial

Iam not connected to internet:(

---

### Post by kpkeerthi on 2009-04-29
Why not install from the repositories? Applications -> Add/Remove

---

### Post by mahenkpatel on 2009-04-29
> **kpkeerthi said:**
> Why not install from the repositories? Applications -> Add/Remove

I cant access internet, that is why i've asked for help.

---

### Post by AXeS on 2009-04-29
> **kpkeerthi said:**
> Why not install from the repositories? Applications -> Add/Remove


Using the 9.04 disc?

---

### Post by kpkeerthi on 2009-04-29
You can find the debs here: [http://archive.ubuntu.com/ubuntu/pool/main/w/wvdial/]("http://archive.ubuntu.com/ubuntu/pool/main/w/wvdial/")

The dependencies of wvdial can be found here: [http://packages.ubuntu.com/jaunty/wvdial]("http://packages.ubuntu.com/jaunty/wvdial")

---

### Post by anaconda on 2009-04-29
WHAT!!!!

Wvdial isn't included in 9.04  ?????

Why an earth would they drop it when more and more people are connecting to internet with 3G-modems?  And wvdial was the easiest pre-installed way to connect with those. (And wvdial is a VERY SMALL program, which also has a few dependencies, so it is hard to install without apt-get)

Is gnome-ppp pre-installed?

is wvdial on the install disk, but not installed by default? (it is possible) 
To try you can insert the CD, and open synaptic. it should configure the cd as a repository.

I read about a manual way to dial using ppp from archlinux wikipages, but didn't succeed with it.

---

### Post by mahenkpatel on 2009-04-29
> **kpkeerthi said:**
> You can find the debs here: [http://archive.ubuntu.com/ubuntu/pool/main/w/wvdial/]("http://archive.ubuntu.com/ubuntu/pool/main/w/wvdial/")

The dependencies of wvdial can be found here: [http://packages.ubuntu.com/jaunty/wvdial]("http://packages.ubuntu.com/jaunty/wvdial")

wvdial have dependencies and the dependencies itself has lots of dependencies and the chain never ends.....how do i know that which components are installed and which i need to download.

Is there any other simpler way to install wvdial without internet???

Annoying things like this restrict me to use Linux as my primary OS.

---

### Post by kpkeerthi on 2009-04-29
Did you check if wvdial's direct dependencies are already installed?

```
dpkg -l | grep -i <package-name>
```

---

### Post by mahenkpatel on 2009-04-29
Iam posting this from ubuntu.........yes guys its done.......iam connected now.

I just installed direct dependencies of wvdial and now its working.

thanks all of you and especially kpkeerthi for sparing ur valuable time and helping me.

regards
Mahendra Patel

---

### Post by kpkeerthi on 2009-04-29
Glad you sorted it out. Cheers.

---

### Post by shazoor on 2009-05-11
I am also facing the same problem. I just installed 9.04 today and now I can't use internet through gprs.

But the way you sought out the trouble, I think same would be the case for me.

Please tell me how I can install the direct dependencies if I am not having internet connection at all. or I have to download it on windows. If so, then from where. Please guide me.

---

### Post by ahsaeed on 2009-05-11
hi 

just install gnome-ppp that will give u 2 benefits:.

1- that will generate wvdial.conf automatically.
2- you will have a GUI interface to connect the internet.. with gppp.
good luck.

---

### Post by shazoor on 2009-05-11
I cant use internet on my desktop without gprs. So, how can I install any other thing. To use internet I need to have wvdial which is not included in 9.04 version on Ubuntu.

---

### Post by pauna on 2009-05-11
> **shazoor said:**
> I cant use internet on my desktop without gprs. So, how can I install any other thing. To use internet I need to have wvdial which is not included in 9.04 version on Ubuntu.

Well, I use my 3G connection via the standard Network Manager, I don't use wvdial anymore. I have a Huawei E170 3G USB stick.

Go to the Network Manager applet, and click to the configuration screen. You should see a Broadband tab. Make a new service provider with relevant data (phone number, access point name, possibly username etc) and it should work just fine. There's also an option for launching the 3G connection automatically when you insert the stick, so you don't even have to manually do anything.

---

### Post by shazoor on 2009-05-12
Now I have completely sorted out. Actually there was no need to install wvdial and the stuff. I was not able to download data packets through the phone even after establishing the connection because there is a setting in NetworkManager Applet which makes the packet data available on pc also.

under configuration select the connection > under ipv4 settings > select Automatic (PPP).

Its done.

---

### Post by ramp.subbu on 2009-10-06
hi ..i have the same problem in installing wvdial package for 3g connection

im have tata photon whiz ..huwaei ec121 .. i did the network connections changes as mentioned in the previous post..... wats next ?? i mean how do i connect ???

---

