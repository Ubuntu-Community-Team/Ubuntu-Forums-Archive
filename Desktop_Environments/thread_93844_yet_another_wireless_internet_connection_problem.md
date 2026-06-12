---
title: "yet another wireless internet connection problem"
date: 2005-11-22
forum: Desktop Environments
---

### Post by ren wins on 2005-11-22
ok SO, i'll start from the begining, b/c i've been wrestling with my wireless internet for way to long(a week?) and i'm tired of dicking around with it

i am running edubuntu (ubuntu 5.10) on my AMD xp 2200+ processor, i have 512mb of ram and a 802.11b PCI wireless card. i forget the exact model, but according to the device manager, it's a texas instruments ACX 111 54Mbps wireless interface

when i first installed edubuntu, i stumbled through the wireless install and set the IP address manually. it worked more or less alright, which was a GREAT relief b/c i first tried to use it w/ Suse 9 pro and that was the reason i went back to windows.  at anyrate, i was having issues with the connection breaking, and i didnt know any terminal commands to repair it or programs to make it keep working, so i would have to  restart my computer all the time. (since i installed the nvidia drivers, every time i try to shutdown restart or logout the computer freezes in one of several interesting fasions, resulting in a power-strip special) someone on some forum suggested using dhclient to reset? i think? i forget which forum (i've been through a couple) and i only really remember to look it up after my internet breaks.  i found out that only works with DHCP, so i changed my connection to DHCP using the network manager GUI and it worked great! until i shut down my computer

this was 2 days ago, and i've gone back to using my dad's old laptop for internet. it's a windows XP machine, as are the rest of the computers in my house... i dont know if that's a problem or not.
i've tried turning the computer back to manual IP whatever... but it hasnt worked. i think i may be missing a part to the set-up

oh, i tried installing networkmanager, but it doesnt seem to want to open for me (using both the icon in the filetree and the nm-aplet command in terminal)

oh, the router is a 2wire 802.11g thing that came w/ our subscription to SBC DSL

i just want to have working internet on my computer, as far as i'm concerned, without internet, computers arent good for much. i would have gone to wired internet (i have a PCI ethernet card installed, but it's not plugged in) but i couldnt find the DSL modem i coulda sworn i had lying around. 
i'm almost to the point of getting a plain 'ol ubuntu disk and starting over from scratch, but the way everyone talks about linux, that'd be like turning a TV off with a brick.

help me obi wan! you're our only hope!

---

### Post by ren wins on 2005-11-22
i just found a bunch of stuff out about my router... if you guys need any particular information about it, i think i may be able to find it

as well as stuff about my actual computer, i just have to copy it over to this laptop w/ a jumpdrive... so ask and you shall receive!

---

### Post by ren wins on 2005-11-23
bumping b/c i'm really close to just wiping the partition and starting over from scratch

:(
but i'd really rather not

---

### Post by HankB on 2005-11-24
Don't wipe yet.

Most likely, the name of your wireless interface is wlan0. You can type the following command to see if it sees your base station:

sudo iwlist wlan0 scan

When I do this with my interface, I see my base:
```
root@baobab:~# iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:0F:B5:23:3A:BE
                    ESSID:"orthanc"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=41/94  Signal level=-54 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100

```

The command to stop your interface is:
    sudo ifdown wlan0
and to bring it up:
    sudo ifup wlan0

This is what works for me. I have configured my interface with a WEP key. It does not come up automagically. I have to run ifup every time I need to connect. But it is a laptop and I regularly pull the card out and suspend when I'm out of the house.

ifup will run the command to fetch the IP address and ifdown will kill the process so it doesn't renew the address.

HTH,
hank

---

