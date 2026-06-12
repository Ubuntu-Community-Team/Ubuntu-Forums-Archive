---
title: "Kubuntu on dell duo, wireless problems"
date: 2011-07-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jeff84 on 2011-07-12
Hi all, i am a new user of kubuntu.
i installed it along side windows 7 on my dell duo, it installed fine no errors. the only problem so far is the wireless configuration.
if i click on the network manager? it says that the wireless is disabled by hardware. run this commands in terminal and this is what is displayed:
iwconfig:

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off



lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:84 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6240 (6.2 KB)  TX bytes:6240 (6.2 KB)

i did already looked in the bios and the card is enabled, also it works great in windows7.
finally i tried to run this command "lspci | grep Wireless" and i got:
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev01)
then i tried this "ifconfig wlan0 up" and got this "SIOCSIFFLAGS: Operation not possible due to RF-kill"

to me it seems that the card is up and running, but for some reasone it is not working right at all.

Any help in figuring this out would be greately appreciated!!!
Thanks,

Jeff

---

### Post by jeff84 on 2011-07-14
never mind found the problem. it was virtual box on kubuntu side, it was confusing the nic.
thanks anyway!

jeff

---

