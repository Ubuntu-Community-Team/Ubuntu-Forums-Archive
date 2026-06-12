---
title: "can't get wireless up and running"
date: 2005-09-20
forum: Desktop Environments
---

### Post by wraparound on 2005-09-20
Hello, I figured i would start a new thread seeing that hours of googling and forum reading hasn't helped.

I am a former Ubuntu user and figured it would be the same with  kubuntu... maybe that's where i'm wrong.

I guess it's easiest if i specify what i've done so far to try to get my wireless connection up and running

1/ kynaptic to get ndiswrapper utils and linux 2.6.10-5-386 headers
( in order to specify the link between /usr/src..... and lib/modules before starting ndiswrapper)

2/ran ndiswrapper ( just like for kubuntu, with my broadcom bcmwl5 driver )
ended up with driver installed and hardware present

3/ iwconfig gives me wlan0 with correct information except not connected to a network ( no worries did that with ubuntu as well, so need to change radio state from 1 to 0)

4/ activate a root login and enable it in kdmrc ( using nano)

5/ log out and log back in as root to change the .conf file in the /etc/ndiswrapper/driver in order to change the radiostate

6/ when i  run iwconfig at this time... i get the same feed as before: no ESSID, no network basically

when running sudo iwlist wlan0 scan .... i don't get any networks listed

7/ i run controle center and go into network settings.  ( as root i have access to administrator mode ) i conifgure the wlan0 that appears under eht0 to dhcp enabled ... I apply... and then the card is activated i see it is given the ip:192.168.1.100... nice little green checkmark

8/ i test internet... no can do....

9/ i run iwconfig and iwlist they show the following

iwconfig

wlan0 IEEE 802.11a ESSID: "linksys"
Mode:Managed Frequency:2.462 GHz Access Point: 00:0C:41:74:C1:46
Bit Rate:54 Mb/s Tx-Power:14 dBm
RTS thr:2347 B Fragment thr:2346 B
Power Managementff
Link Quality:100/100 Signal level:-68 dBm Noise level:-256 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:4 Invalid misc:1347 Missed beacon:0

and iwlist 

wlan0     Scan completed :
          Cell 01 - Address: 00:0C:41:74:C1:46
                    ESSID:"linksys"
                    Protocol: IEEEE 802.11b
                    Mode:Managed
                    Frequency:2.462GHz (channel 11)
                    Quality:0/100  Signal level:-68 dBm  Noise level:256 
dBm
                    Encryption key:off
                    Bit Rate:1Mb/s
                    Bit Rate:2Mb/s
                    Bit Rate:5.5Mb/s
                    Bit Rate:11Mb/s
                    Bit Rate:18Mb/s
                    Bit Rate:24Mb/s
                    Bit Rate:36Mb/s
                    Bit Rate:54Mb/s
                    Bit Rate:6Mb/s
                    Bit Rate:9Mb/s
                    Bit Rate:12Mb/s
                    Bit Rate:48Mb/s
                    Extra: bcn_int=100
                    Extra: atim=0


If anyone has an answer.... i'd really appreciate it... because somehow.... all this works on Ubuntu..... but it just doesn't on Kubuntu. I've now been installing uninstalling, running all the variants i can find on forums... but no can do....
i'd really hate to have to go back to Ubuntu ( can't stand gnome )

O.2

---

### Post by wraparound on 2005-09-20
ok.... partially fixed the problem

sudo dhclient wlan0 gets it up and running

however i'm still stuck with the problem that after every login i have to 
sudo modprpobe ndiswrapper
followed by sudo dhclient wlan0 to get it up 

ndiswrapper -m doesn't do what it did for ubuntu...

guess i have to figure out a script for start up on sessions... anyone can help me out here ??

( to think that i had left linux back in 1997... way before all this complicated stuff... where we would just think that our system monitors were so cool ....)


cheers

---

