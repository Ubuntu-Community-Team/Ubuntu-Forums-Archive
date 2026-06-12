---
title: "Networking Difficulties"
date: 2008-01-15
forum: Dell  Ubuntu Support
---

### Post by avmasala on 2008-01-15
I am totally new to Linux.  Just did a complete install on my Inspiron 1501.  Cannot connect via hard wire or wireless.  Hard wire connection is recognized to my Westell 2200 modem (I have Verizon DSL), but Firefox does not connect.  I have attempted some of the fixes noted here, but nothing seems to work.  HELP!!

---

### Post by natehall on 2008-01-16
Applications > Accessories > Terminal
Type in    iwconfig    and post the results here.

---

### Post by avmasala on 2008-01-16
lo        no wireless extensions. 

eth0      no wireless extensions. 

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311" 
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off 
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by memoryproblems on 2008-01-16
greetings, I also have a dell Inspiron 1501 laptop which I have installed Gutsy on. I don't have a solution, I'm very interested in what help people can shine on this problem because I have been doing everything I can think of, even asking for help several times on these forums (with no luck). I am trying to connect to a wireless network. I haven't really had any problems hooking into a wired connection, however the other day I tried installing from the live-cd/installation cd's that ubuntu sends out for free. My system wouldn't connect using a wired connection, however I haven't ever seemed to have any problems with it when I've installed from the alternate-install cd (also, with the live-cd install, my system sat with a blank screen for about twenty seconds after the grub boot loader before it began loading, and with the alternate cd its always starts right away), so you might try with the alternate install cd.

As far as I know, my Dell uses a wireless card named the Dell WLAN 1390. This uses a broadcom bcm43xx chipset, i think the entire number for mine is something like bcm94311xxx there are three letters appended to the end, but I don't beleive they are relevant. The kernel included in Gutsy seems to have some help for this chipset, If you go under restricted drivers manager, you can get the networking to work pretty easily, all you have to do is install bcm43xx-fwcutter and download the firmware (which is available freely on the web). You can find good instructions of what to do with the restricted driver manager here: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy).

On my system, this gets the networking to work like a charm, no problems with that, however I believe there must be some problem with the kernel, because if I have my networking card on, my keyboard will stop working. (keep in mind that this is a laptop with an integrated keyboard, although I did attempt to hook up an external usb keyboard, and that didn't work either.) Basically the keyboard won't recognize any input, even when i try fn+f2 to try to deactivate the networking card, but when I deactivate it as soon as I log in, my keyboard will keep normal function. 

If anybody has any suggestions to this, I'd love to hear them, I've been struggling with this problem for quite some time, but haven't found any solutions, I've tried NDISwrapper, however it doesn't seem to want to connect very well, and it'll lose connections and then refuse to reconnect, so it doesn't seem like its a very stong option.

thanks,
Dennis

---

