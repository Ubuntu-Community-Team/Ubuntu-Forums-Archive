---
title: "Real Flight 4.5"
date: 2010-02-15
forum: Gaming &amp; Leisure
---

### Post by aftcg on 2010-02-15
Hi everyone!!

I LOVE LOVE LOVE this forum, and despise the fact that I can only run Real Flight R/C Flight Simulator on my WVista partition.  BTW, the only game I have on my W partition...

BUT, being a n00b, I don't know how to make this program work on Linux, or U9.10.  

Please help.  There has to be another RC pilot out there that can make RF 4.5 run on U9.10!!!

UF'ers, I'm counting on you!

Love,
the AFTCG

---

### Post by Siph0n on 2010-02-15
I don't use Real Flight 4.5, tho I do own 3.5 I think. Just wanted to say you aren't the only rc pilot on these forums. Do you fly helicopters or airplanes?

---

### Post by aftcg on 2010-02-20
I'm an airplane guy I guess.  Mostly do 3D with profiles.  

I see on knifedge.com that guys are trying to run RF on a windows VM, bu they can't get the usb to work through the vm I guess.  

I can't believe none of us RC geeks have figured out how to make RF work on linux.

---

### Post by Dantheman53 on 2010-02-21
Fellow rc flyer here, mostly heli :D There is a native RC simulator but i have never tried it.

[http://www.playdeb.net/software/CRRCsim](http://www.playdeb.net/software/CRRCsim)

---

### Post by hbj on 2011-03-27
I was not able to get the above link to work on 10.10, but CRRSIM is easy enough to install yourself.  I already have many development libraries installed, so I'm not sure if you will need to install any others, but this is all I needed to build and install it on my system:

```
sudo apt-get install libsdl-dev libplib-dev portaudio19-dev libjpeg62-dev

```

I downloaded crrsim-0.9.11.tar.gz and then ran:

```
cd Downloads
tar -zxf crrsim-0.9.11.tar.gz
cd crrsim-0.9.11
./autogen.sh
./configure --prefix=/opt/crrsim --exec-prefix=/opt/crrsim
make
sudo make install
```

After you run the configure script, check for any error messages.  It did complain that it preferred version 18 of the portaudio sound library, but I ignored that and it seems to run fine.  After you successfully build and install the software, you can run it from a terminal window or by configuring a launcher.  Since I chose to install it into /opt, I launch it with the command:

```
/opt/crrsim/bin/crrcsim
```

---

