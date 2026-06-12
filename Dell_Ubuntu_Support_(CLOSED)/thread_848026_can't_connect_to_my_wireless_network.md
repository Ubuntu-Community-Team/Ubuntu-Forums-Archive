---
title: "can't connect to my wireless network"
date: 2008-07-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by enroc on 2008-07-03
Hi,

I have a Dell Dimension 5150 + Dell Wireless USB 1450 and Ubuntu 8.04 installed on it.

But the network I always connect to with Windows XP is not reachable under Ubuntu.

I can connect to very close networks. I first thought it was the WPA but after I tried that on a test router it seems ok.

This is the way it doesn't work:

[[IMG]http://83.161.24.58/~corneb/1_m.jpg[/IMG]]("http://83.161.24.58/1.jpg")
Choose the network.
[[IMG]http://83.161.24.58/~corneb/2_m.jpg[/IMG]]("http://83.161.24.58/2.jpg")
Fill in the key.
[[IMG]http://83.161.24.58/~corneb/3_m.jpg[/IMG]]("http://83.161.24.58/3.jpg")
It tries to connect.
[[IMG]http://83.161.24.58/~corneb/4_m.jpg[/IMG]]("http://83.161.24.58/4.jpg")
Fail.

Can someone please help me out?

---

### Post by enroc on 2008-07-03
Ok a little update
I plugged the usb adapter into a dell inspiron 5100
ran the live cd
connect when i was very close to the access point
and it worked but it was still 85% (signal strength)

why is the signal of the receiver so weak in ubuntu compared to xp?
because I still can't connect from my room upstairs..

thanks in advance

edit: I walked upstairs and the signal kept stable :S
So it appears that I need to connect close to the AP and then it doesn't matter anymore.
Unfortunately this is not an option for my Dimension.

---

### Post by kiko72 on 2008-07-04
Interesting - I have a similar problem with a 1501 laptop. I have difficulty connecting to signals in Ubuntu.

I just installed the 64-bit 8.04, and was amazed to see that wireless was actually working - it never did in 7.04 and was on my list of things to sort out during this migration to a new OS. However, I know one of my neighbours does not secure his wireless signal and it's a good test. I can connect to the signal in XP easily, but not at all in Ubuntu.

Very weird.

As you, I can connect to signals that are very close by and get good strength. I just find it odd that there is any difference in range.

I wish I had an answer for you!

---

### Post by enroc on 2008-07-05
The problem is solved now.

I posted at [http://lists.us.dell.com/pipermail/linux-desktops/2008-July/001608.html](http://lists.us.dell.com/pipermail/linux-desktops/2008-July/001608.html)

And they talked about iwconfig
So I started to play with iwconfig and I noticed that it didn't want to set the channel to 12 and 13.

After I set the channel to 2, it's working.

@kiko72
Yes, after 7.10 wireless was actually working but I didn't know it was the channels until now.
So maybe it works for you too.

---

### Post by kiko72 on 2008-07-07
So, uh, the "12" in...

# iwconfig wlan0 ap 00:08:12:ac:ef:12

...is the channel of the access point? Did that sentence even make sense? :) I've never messed around with iwconfig before, and I don't even have my own wireless set-up - I just need to have Ubuntu more mobile. I don't want to *have* to use XP on a train or in a cafe, for instance.



The output of my iwconfig wlan0 is...


wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

