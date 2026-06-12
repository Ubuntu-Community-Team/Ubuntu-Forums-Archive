---
title: "wlan0 installed but no access"
date: 2006-02-18
forum: Desktop Environments
---

### Post by isceald on 2006-02-18
I'm new to ubuntu with very little prior unix experience.  I just installed ubuntu and everything is great except for the wireless.  I've scoured the web and tried everything i could find -- but it's still not working.

I've installed a Quetec ASW2310 using ndiswrapper.  The card shows up on ndiswrapper -l (driver present, hardware present) and on iwconfig.  

iwconfig output:
IEEE 802.11b  ESSID: off/any
Mode: Managed Frequency: 24.412 GHz Access Point: 00:00:00:00:00:00
Bit rate: 1 Mb/s
RTS thr: 2428 B  Fragment thr: 2428 B
[Remaining items all show 0]

Pinging localhost works
Pinging 192.168.1.1 - Destination host unreachable

iwlist wlan0 scan - No scan results.

The card is visible and activated in Networking.  I have set IP config to DHCP.

My windoze laptop in the same room is accessing the wireless LAN.  The green light on the card (ubuntu machine) is flashing.

Can anyone help?  Thanks!

---

### Post by nalmeth on 2006-02-18
huh, to all appearances it should be working!

all I can do is point you to here, but it sounds like you've likely been there already:
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

post any new information you might find

EDIT: Stupid obvious question? Probably... But did you go into SETTINGS --> ADMINISTRATION --> NETWORKING and activate the wlan0 device? Thought it was worth asking anyway!

---

### Post by isceald on 2006-02-18
yes, i've tried the troubleshooting wiki... and yes, i went into Networking and activated the card.  But thanks for replying. :)

---

### Post by nalmeth on 2006-02-18
hmm might want to check into madwifi, and see if you're supported.

keep at it, and keep posting progress

good luck!

EDIT: also, I've heard that newer versions of ndiswrapper perform better, maybe it will make yours work.

---

### Post by hiikeeba on 2006-02-19
I was having the same problem with a Compaq USB wireless adapter.  I downloaded ndiswrapper 1.10, and installed that through synaptic, and TA-DAH!, I'm online.

---

### Post by joysa on 2006-02-19
:confused: hi Gys!

I'm very confused baout ubantu performance...i've got a long story but dn't wanna bother you as i'm havin a situation over her.

my PC: intel 800 MHZ
ram :192 MB
ati graphix card
**WiFi connection **

USB adaptor : WUSB54G (Linksys)
Chip ID: 13b1 : 000d

my problem: everthin is juz fyn n doing well except my WiFi adaptor,i've go thru the "**ndiswrapper**" HowTo process provided by Ubantu Forum Support,but it seems Problem Presist,the adpator is installed and ***ndiswrapper -l*** command shows driver installed juz lyk the poster command but can't see any *WLAN()* device in ***ndisgtk *** menu,and still can't get access of net ...tried severel ways to get it works but seems,ubantu dosen't suit me:???: waht steps i should do...

O,aniwe i'm a newbi,so any advise about installing mp3/mpeg codec on ubantu will be apprichiated.

thnx n loking foroward to hearing from some Genious...:-k 

personal Email Wellcome: [email]mamun.joy@gmail.com[/email]

---

### Post by baillieboy on 2006-02-21
I have almost exactly the same problem, except I dont have to use ndiswrapper as ubuntu has already recognised the card and installed a driver. (acx_pci)

For all intents and purposes the wireless card is working, but it will not connect to the router...it's driving me crazy! Any help would be great!

---

### Post by isceald on 2006-02-26
ok!  I finally figured out how to upgrade to ndiswrapper 1.10 (easy when you know how!*) and my card is working!  

meanwhile, I also bought a new wireless card, Trendnet TEW 423PI, thinking that it had a linux driver.  It doesn't -- so I still have to use ndiswrapper.  (I also tried some other weird things, like installing a driver for my k7 processor, but we won't talk about those.)  So the newer ndiswrapper may have worked with the old card as well.

__

*Here's how:
remove the old ndiswrapper using synaptic  (I could not figure out how to see the new one from synaptic)
Download ndiswrapper1.10.tar.gz
Open a terminal (from applications/accessories)
from the directory where you have placed it, gunzip ndiswrapper-1.10.tar.gz
tar xvfz ndiswrapper-1.10.tar
cd ndiswrapper-1.10
make
make install

(I may have had to use sudo with some of these commands -- don't remember which.)

After I did this and rebooted, the driver which I had installed under the old ndiswrapper was already installed.  I had to reactivate the card, but when I did "wlist wlan0 scanning"  the card was finding the access point for the first time.  Then I had to go back in and add the ESSID of the network in Networking.  When I tried firefox, everything (like my keyboard!) stopped working, but after reboot and recover, it's all fine.

Thanks everyone for the suggestions!

isceald

---

### Post by wisdoms on 2006-03-01
I reinstalled Kubuntu 5.10 and the wireless connection doesn't work!
Everything works fine with the driver and the commands (iwlist, iwconfig, ...) but I cannot get the access point MAC address, this command 

iwconfig wlan0 ap xx:xx:xx:xx:xx 

seems useless! In fact "iwcinfig wlan0" returns "Access Point: 00:00:00:00:00:00" !!!!!!!!!
I have tried also without encryption, but nothing has changed! 
Please reply!!! :)

---

### Post by deathbyswiftwind on 2006-03-01
i couldnt get my broadcom to work under Kubuntu following the same guide i used for ubuntu. i finally game up switched back to ubuntu and just apt got kde and it works like a charm

---

