---
title: "I seriously can't get ndiswrapper to work. Please help :("
date: 2005-12-28
forum: General Help
---

### Post by mr.karmalicious on 2005-12-28
Hello there.  I was following [this](https://wiki.ubuntu.com/SetupNdiswrapperHowto) tutorial to try and install ndiswrapper for my WMP54G PCI Card. It was all well and good until I got to step 4, where I had to type 'modprobe ndiswrapper' into the terminal. It then said "FATAL: Module ndiswrapper not found." How could this be, if the other steps, which used ndiswrapper (I think) worked fine? 

I really don't know what's going on :(...

BTW, if it's not sickeningly obvious, I'm asolutely new to Ubuntu, and Linux as well. Any help would be greatly appreciated...

mrk

---

### Post by M4VE on 2005-12-28
what happens when you type ndiswrapper -l?  Is it spitting out that the driver is present and the hardware is available?  The order of things in your wiki seems a bit backwards from the book I have.  Anyway, hope you get it working, if -L doesn't show you what you want, then it's not installed, which is why it's fatally failing.

---

### Post by mr.karmalicious on 2005-12-28
Thank you for the fast response. Apparently, that works...

This is the output.

```
Installed ndis drivers:
bcmwl5  driver present, hardware present

```

Funny?

---

### Post by antiemptyv on 2005-12-28
I couldn't get ndiswrapper to work using that tutorial either for some reason...  not sure why.  When I followed [this one]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation"), however, it worked.  I've got a different wireless adapter than you do, but maybe this will work for you, too.

< [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation) >

Good luck,
Matt

---

### Post by The Mekon on 2005-12-28
It would appear that ndiswrapper is working and has installed the drivers correctly.

Try typing iwconfig to see if you can see the wireless adapter. I get

brian@fonze-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Edwards"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:3D:28:63:B7
          Bit Rate:24 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=33/94  Signal level=-62 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

Which shows my adapter as ath0.

If you can see your adapter you should be able to set it up using:

System/Admistration/Networking.

---

### Post by mr.karmalicious on 2005-12-28
Okay, I typed iwconfig.

```
root@Computar:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

```

I'm just a barrel of luck...

PS: Thanks for the help, guys :).

---

### Post by The Mekon on 2005-12-28
There was a post earlier about wireless installation using ndiswrapper.

Try[ here]("http://www.ubuntuforums.org/showthread.php?t=91732")

---

### Post by mr.karmalicious on 2005-12-28
Okay, I tried following the instructions.

```
sudo vi /etc/network/interfaces
```

When I got to that point, and I opened the file, I added the stuff that it said to. I accidentally hit enter a few times...somewhere, so if somebody could take a screenshot of theirs so I can fix mine, it would be great. I think that that (what I just explained) is the reason it's not working, because when I try to type 

```
sudo ifup wlan0

```

it displays

```
/etc/network/interfaces:20: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"

```

*sigh*

---

### Post by d11wtq on 2005-12-28
Well... it sounds like you ran `make' which failed to compile the drivers (which isn't neccessarily obvious unless you read the results) but you went on to run `make install'.  Therefore you have the ndiswrapper binary but no modules installed for it ;)

What does /usr/src/linux point to?

```

ls -l /usr/src/linux

```

Also... did you install ndiswrapper from apt-get or do it manually?  apt-get should set it up for you.

---

