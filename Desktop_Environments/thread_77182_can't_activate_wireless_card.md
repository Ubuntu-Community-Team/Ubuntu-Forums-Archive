---
title: "can't activate wireless card"
date: 2005-10-16
forum: Desktop Environments
---

### Post by net_benjo on 2005-10-16
Hi,

Here's my situation.  I installed Breezy yesterday on my hp dv4170 laptop.  

First, when I boot up my laptop without any wired ethernet connection it takes really long time to get past "checking network interfaces" step.  It spend about at minute on that step alone.  

Second, after booting, if I type iwconfig I get the following output:
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11g  ESSID:"bosna"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:13:46:1D:A1:A0
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/100  Signal level=-58 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:13   Missed beacon:23

sit0      no wireless extensions.

But, when I right click on 'network' icon in the right of the top panel and select properties I only have to optins for connecitons: eh1 and lo.  But no eth0.  

Third, I try turning on my wireless by pushing the button on my keyboard, but it doesn't turn it on. (i.e. the light stays off).

Then I go to system>>administration>>networking and see that eth0 connection is marked as active.  I decativate it, then check that DHCP is selected for it, and activate it again.  

Even after this, eth0 does not appear in the connection options.  I still only get eth1 and lo.  when I type iwconfig now I get:

lo        no wireless extensions.

eth1      no wireless extensions.

eth0      radio off  ESSID:"bosna"
          Mode:Managed  Channel:0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=off
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:13   Missed beacon:0

sit0      no wireless extensions.

Does anybody have any ideas for me?  I just can't seem to turn on wireless.

thanks

---

### Post by HermanAB on 2005-10-16
You may need to install a Windows driver.

See this guide, it describes a number of ways to get going, using ndiswrapper and LinuxAnt:
[http://www.aerospacesoftware.com/notebook-howto.html](http://www.aerospacesoftware.com/notebook-howto.html)

Cheers,

Herman

---

### Post by apu95 on 2005-10-16
that little lag part also happens to me if it can't find a wireless connection.

you have the DV4170....you probably have an intel wireless card then? or broadcom?

---

### Post by akseli on 2005-10-16
[QUOTE=net_benjo]Hi,

Here's my situation.  I installed Breezy yesterday on my hp dv4170 laptop.  

First, when I boot up my laptop without any wired ethernet connection it takes really long time to get past "checking network interfaces" step.  It spend about at minute on that step alone.  

Second, after booting, if I type iwconfig I get the following output:
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11g  ESSID:"bosna"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:13:46:1D:A1:A0
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/100  Signal level=-58 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:13   Missed beacon:23

sit0      no wireless extensions.

But, when I right click on 'network' icon in the right of the top panel and select properties I only have to optins for connecitons: eh1 and lo.  But no eth0.  

Third, I try turning on my wireless by pushing the button on my keyboard, but it doesn't turn it on. (i.e. the light stays off).

Then I go to system>>administration>>networking and see that eth0 connection is marked as active.  I decativate it, then check that DHCP is selected for it, and activate it again.  

Even after this, eth0 does not appear in the connection options.  I still only get eth1 and lo.  when I type iwconfig now I get:

lo        no wireless extensions.

eth1      no wireless extensions.

eth0      radio off  ESSID:"bosna"
          Mode:Managed  Channel:0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=off
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:13   Missed beacon:0

sit0      no wireless extensions.

Does anybody have any ideas for me?  I just can't seem to turn on wireless.

thanks[/QUOTE]

Once you get your connections setup (sorry but I don't have the time to try to solve it now) you should download network-manager which is an excellent application for wired and wireless connection management.

---

