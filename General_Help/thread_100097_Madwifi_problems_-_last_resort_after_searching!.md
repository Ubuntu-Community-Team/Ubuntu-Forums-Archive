---
title: "Madwifi problems - last resort after searching!"
date: 2005-12-06
forum: General Help
---

### Post by Auto|MaG on 2005-12-06
Been trying to get these madwifi drivers installed for my WG511T card, with no luck. Ive tried a few different times, and always get errors after doing a # make. Ill post the errors here, and see if anyone has some ideas. I thought it might be something simple like a missing symlink or something, but I dont know enough yet to verify that. I started by downloading the madwifi-cvs-current.tar.gz - extracting it, getting sharutils, linux-headers and linux-source and so on. Heres the error I get when doing make (also errors on MAKE INSTALL)

```
root@ubuntu:/usr/src/madwifi# make
Checking if all requirements are met... ok.
mkdir -p ./symbols
for i in ./ath_hal ath_rate/sample ./net80211 ./ath; do \
        make -C $i || exit 1; \
done
make[1]: Entering directory `/usr/src/madwifi/ath_hal'
cp ./../hal/linux/ah_osdep.c ah_osdep.c
uudecode ./../hal/public/i386-elf.hal.o.uu
cp ./../hal/public/i386-elf.opt_ah.h opt_ah.h
make -C /usr/src/linux-headers-2.6.12-10-386 SUBDIRS=/usr/src/madwifi/ath_hal MODVERDIR=/usr/src/madwifi/ath_hal/../symbols modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /usr/src/madwifi/ath_hal/ah_osdep.o
  LD [M]  /usr/src/madwifi/ath_hal/ath_hal.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /usr/src/madwifi/ath_hal/.hal.o.cmd for /usr/src/madwifi/ath_hal/hal.o
  CC      /usr/src/madwifi/ath_hal/ath_hal.mod.o
  LD [M]  /usr/src/madwifi/ath_hal/ath_hal.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make[1]: Leaving directory `/usr/src/madwifi/ath_hal'
make[1]: Entering directory `/usr/src/madwifi/ath_rate/sample'
make -C /usr/src/linux-headers-2.6.12-10-386 SUBDIRS=/usr/src/madwifi/ath_rate/sample MODVERDIR=/usr/src/madwifi/ath_rate/sample/../../symbols modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /usr/src/madwifi/ath_rate/sample/sample.o
In file included from /usr/src/madwifi/ath_rate/sample/sample.c:47:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  LD [M]  /usr/src/madwifi/ath_rate/sample/ath_rate_sample.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /usr/src/madwifi/ath_hal/.hal.o.cmd for /usr/src/madwifi/ath_hal/hal.o
*** Warning: "ieee80211_iterate_nodes" [/usr/src/madwifi/ath_rate/sample/ath_rate_sample.ko] undefined!
*** Warning: "ether_sprintf" [/usr/src/madwifi/ath_rate/sample/ath_rate_sample.ko] undefined!
  CC      /usr/src/madwifi/ath_rate/sample/ath_rate_sample.mod.o
  LD [M]  /usr/src/madwifi/ath_rate/sample/ath_rate_sample.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make[1]: Leaving directory `/usr/src/madwifi/ath_rate/sample'
make[1]: Entering directory `/usr/src/madwifi/net80211'
make -C /usr/src/linux-headers-2.6.12-10-386 SUBDIRS=/usr/src/madwifi/net80211 MODVERDIR=/usr/src/madwifi/net80211/../symbols  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /usr/src/madwifi/net80211/if_media.o
In file included from include/linux/if_ether.h:107,
                 from include/linux/netdevice.h:29,
                 from /usr/src/madwifi/net80211/if_media.c:60:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  CC [M]  /usr/src/madwifi/net80211/rc4.o
  CC [M]  /usr/src/madwifi/net80211/ieee80211.o
In file included from /usr/src/madwifi/net80211/ieee80211.c:45:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  CC [M]  /usr/src/madwifi/net80211/ieee80211_crypto.o
In file included from /usr/src/madwifi/net80211/ieee80211_crypto.c:43:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  CC [M]  /usr/src/madwifi/net80211/ieee80211_input.o
In file included from /usr/src/madwifi/net80211/ieee80211_input.c:44:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  CC [M]  /usr/src/madwifi/net80211/ieee80211_node.o
In file included from /usr/src/madwifi/net80211/ieee80211_node.c:45:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  CC [M]  /usr/src/madwifi/net80211/ieee80211_output.o
In file included from /usr/src/madwifi/net80211/ieee80211_output.c:45:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
In file included from include/linux/ip.h:84,
                 from /usr/src/madwifi/net80211/ieee80211_output.c:47:
include/net/sock.h: In function 'skb_copy_to_page':
include/net/sock.h:992: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
/usr/src/madwifi/net80211/ieee80211_output.c: In function 'ieee80211_pwrsave':
/usr/src/madwifi/net80211/ieee80211_output.c:1638: warning: pointer targets in passing argument 1 of 'ieee80211_dump_pkt' differ in signedness
  CC [M]  /usr/src/madwifi/net80211/ieee80211_proto.o
In file included from /usr/src/madwifi/net80211/ieee80211_proto.c:46:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  CC [M]  /usr/src/madwifi/net80211/ieee80211_wireless.o
In file included from include/linux/if_ether.h:107,
                 from include/linux/netdevice.h:29,
                 from /usr/src/madwifi/net80211/ieee80211_wireless.c:49:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
/usr/src/madwifi/net80211/ieee80211_wireless.c: In function 'read_ap_result':
/usr/src/madwifi/net80211/ieee80211_wireless.c:115: warning: pointer targets in passing argument 4 of 'iwe_stream_add_point' differ in signedness
/usr/src/madwifi/net80211/ieee80211_wireless.c:119: warning: pointer targets in passing argument 4 of 'iwe_stream_add_point' differ in signedness
/usr/src/madwifi/net80211/ieee80211_wireless.c: In function 'encode_ie':
/usr/src/madwifi/net80211/ieee80211_wireless.c:1280: warning: pointer targets in passing argument 1 of 'sprintf' differ in signedness
/usr/src/madwifi/net80211/ieee80211_wireless.c: In function 'ieee80211_ioctl_addmac':
/usr/src/madwifi/net80211/ieee80211_wireless.c:2098: warning: pointer targets in passing argument 2 of 'acl->iac_add' differ in signedness
/usr/src/madwifi/net80211/ieee80211_wireless.c: In function 'ieee80211_ioctl_delmac':
/usr/src/madwifi/net80211/ieee80211_wireless.c:2116: warning: pointer targets in passing argument 2 of 'acl->iac_remove' differ in signedness
  CC [M]  /usr/src/madwifi/net80211/ieee80211_linux.o
In file included from /usr/src/madwifi/net80211/ieee80211_linux.c:38:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  CC [M]  /usr/src/madwifi/net80211/ieee80211_crypto_none.o
In file included from /usr/src/madwifi/net80211/ieee80211_crypto_none.c:41:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  CC [M]  /usr/src/madwifi/net80211/ieee80211_acl.o
In file included from /usr/src/madwifi/net80211/ieee80211_acl.c:51:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  CC [M]  /usr/src/madwifi/net80211/ieee80211_crypto_ccmp.o
In file included from /usr/src/madwifi/net80211/ieee80211_crypto_ccmp.c:42:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  CC [M]  /usr/src/madwifi/net80211/ieee80211_crypto_tkip.o
In file included from /usr/src/madwifi/net80211/ieee80211_crypto_tkip.c:42:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  CC [M]  /usr/src/madwifi/net80211/ieee80211_crypto_wep.o
In file included from /usr/src/madwifi/net80211/ieee80211_crypto_wep.c:38:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  CC [M]  /usr/src/madwifi/net80211/ieee80211_xauth.o
In file included from /usr/src/madwifi/net80211/ieee80211_xauth.c:51:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  LD [M]  /usr/src/madwifi/net80211/wlan.o
  LD [M]  /usr/src/madwifi/net80211/wlan_wep.o
  LD [M]  /usr/src/madwifi/net80211/wlan_tkip.o
  LD [M]  /usr/src/madwifi/net80211/wlan_ccmp.o
  LD [M]  /usr/src/madwifi/net80211/wlan_acl.o
  LD [M]  /usr/src/madwifi/net80211/wlan_xauth.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /usr/src/madwifi/ath_hal/.hal.o.cmd for /usr/src/madwifi/ath_hal/hal.o
  CC      /usr/src/madwifi/ath_rate/sample/ath_rate_sample.mod.o
  LD [M]  /usr/src/madwifi/ath_rate/sample/ath_rate_sample.ko
  CC      /usr/src/madwifi/net80211/wlan.mod.o
  LD [M]  /usr/src/madwifi/net80211/wlan.ko
  CC      /usr/src/madwifi/net80211/wlan_acl.mod.o
  LD [M]  /usr/src/madwifi/net80211/wlan_acl.ko
  CC      /usr/src/madwifi/net80211/wlan_ccmp.mod.o
  LD [M]  /usr/src/madwifi/net80211/wlan_ccmp.ko
  CC      /usr/src/madwifi/net80211/wlan_tkip.mod.o
  LD [M]  /usr/src/madwifi/net80211/wlan_tkip.ko
  CC      /usr/src/madwifi/net80211/wlan_wep.mod.o
  LD [M]  /usr/src/madwifi/net80211/wlan_wep.ko
  CC      /usr/src/madwifi/net80211/wlan_xauth.mod.o
  LD [M]  /usr/src/madwifi/net80211/wlan_xauth.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make[1]: Leaving directory `/usr/src/madwifi/net80211'
make[1]: Entering directory `/usr/src/madwifi/ath'
make -C /usr/src/linux-headers-2.6.12-10-386 SUBDIRS=/usr/src/madwifi/ath MODVERDIR=/usr/src/madwifi/ath/../symbols modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /usr/src/madwifi/ath/if_ath.o
In file included from /usr/src/madwifi/ath/if_ath.c:51:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
/usr/src/madwifi/ath/if_ath.c: In function 'ath_tx_capture':
/usr/src/madwifi/ath/if_ath.c:3304: warning: pointer targets in passing argument 1 of 'strcpy' differ in signedness
/usr/src/madwifi/ath/if_ath.c: In function 'ath_rx_capture':
/usr/src/madwifi/ath/if_ath.c:3461: warning: pointer targets in passing argument 1 of 'strcpy' differ in signedness
/usr/src/madwifi/ath/if_ath.c: In function 'ath_getchannels':
/usr/src/madwifi/ath/if_ath.c:5412: warning: pointer targets in passing argument 4 of 'ath_hal_init_channels' differ in signedness
  CC [M]  /usr/src/madwifi/ath/if_ath_pci.o
In file included from include/linux/if_ether.h:107,
                 from include/linux/netdevice.h:29,
                 from /usr/src/madwifi/ath/if_ath_pci.c:53:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  CC [M]  /usr/src/madwifi/ath/radar.o
In file included from /usr/src/madwifi/ath/radar.c:4:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  LD [M]  /usr/src/madwifi/ath/ath_pci.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /usr/src/madwifi/ath_hal/.hal.o.cmd for /usr/src/madwifi/ath_hal/hal.o
  CC      /usr/src/madwifi/ath/ath_pci.mod.o
  LD [M]  /usr/src/madwifi/ath/ath_pci.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make[1]: Leaving directory `/usr/src/madwifi/ath'
root@ubuntu:/usr/src/madwifi#


```

---

### Post by aclaunch on 2005-12-07
Did I miss something, there are no specific errors just some warnings. (GCC will give lots of warnings if the code is imperfectly written but an error is what counts.

After "make" did you do a "make install"? If not, do that and then run "dmesg". Look at the bottom for lines about your wifi card. If there is nothing, try disconnecting the card and then reconnecting and recheck dmesg. Then let us know.

Good Luck,
Alan

---

### Post by Auto|MaG on 2005-12-07
[QUOTE=aclaunch]Did I miss something, there are no specific errors just some warnings. (GCC will give lots of warnings if the code is imperfectly written but an error is what counts.

After "make" did you do a "make install"? If not, do that and then run "dmesg". Look at the bottom for lines about your wifi card. If there is nothing, try disconnecting the card and then reconnecting and recheck dmesg. Then let us know.

Good Luck,
Alan[/QUOTE]


Hmm, ok...I was assuming some things like "Warning: could not find /usr/src/madwifi/ath_hal/.hal.o.cmd for /usr/src/madwifi/ath_hal/hal.o" were problems occuding after doing the make. I can post my make install log when I get home if that may help. After I did make install, i did 

#modprobe ath_pci

Is that correct? I belive I got something like "ath_pci not found", but ill have to double check. Thanks for the reply though!!

---

### Post by Auto|MaG on 2005-12-07
Some more info, incase anyone can help. I redid make/make install, then did 

modprobe ath_pci
modprobe ath_hal
modprobe wlan

Didn't get any errors, just a promt again so I belive it worked?...I rebooted and after doing a dmsg I see ath_hal,wlan,ath_rate and ath_pci lines in the list. This means the drivers are loaded, correct? The light on my card is blinking also. 

However, if i do iwconfig, i just
lo no wireless extensions
eth0 no wireless extensions
sit0 no wireless extensions

but there is no ath0. Any ideas?

edit: when doing a dmesg, wlan comes after ath_pci and ath_hal...that is not correct is it? I belive that has to come first. How do I edit the order?

---

### Post by aclaunch on 2005-12-08
In rereading this I'm confused: the linux-restricted modules in the repositories have the madwifi driver built-in and I have an Atheros based card in this machine which works fine out of the box. 

That said, the order in dmesg doesn't matter. You have to first set up networking and then setup the card. Try "sudo ifconfig ath0 DHCP" if you use DHCP or "sudo ifconfig ath0 XXX.XXX.XXX.XXX". Then, once that is done, do "iwconfig" see what cards are seen. You should then be able to set up the card via the networking application in System->Admin->Networking.

But, I still think all you need to do is make sure the linux-restricted-modules are there because Atheros is one of the most widely supported chipsets for wifi cards.

Good Luck,
Alan

---

### Post by hajk on 2005-12-08
But why, oh why are you (OP) making life difficult in trying to compile the madwifi driver for your WG511T card? The driver is available in breezy restricted in the linux-restricted-modules... package for the kernel you're running. Only thing: it's not installed by default, so you'll have to fire up Synaptic to install it yourself.
I did this on my old ThinkPad for the WG511T card, works like a charm.:D 

The previous Ubuntu Hoary didn't have this driver, so people needing it had to compile it from source -- but in this forum I expect that you're running Breezy, no? :???:

---

### Post by Auto|MaG on 2005-12-08
Thanks guys! I swear im not trying to give myself a headache. Still trying to figure out how linux works and I was under the impression you had to do this. I was triyng to follow this guide: [http://ubuntuforums.org/showthread.php?t=75451&highlight=howto+madwifi](http://ubuntuforums.org/showthread.php?t=75451&highlight=howto+madwifi) 

Since it sounds like you dont have to do all that, Ill double check those restricted modules, because that would be soooo much easier :p 

Thanks again!

---

### Post by Auto|MaG on 2005-12-08
Ok, I tried # sudo ifconfig ath0 192.168.1.50 but I get an error that says
ath0: ERRORwhile getting interface flags: No such device.

The card is plugged in and the light blinks every 5 seconds or so. Do I have to remove the stuff Ive done with trying to compile the madwifi drivers? I have the restricted-modules-2.6.12-10-386 installed.

---

### Post by aclaunch on 2005-12-08
First check if the module is now loaded "sudo lsmod | grep ath". If yes, you can try unplugging and replugging the card, recheck "dmesg" to see if the card is now recognized. 

If the module is not loaded, try "sudo modprobe ath_pci" and see what the output is.

Alan

Edit: And do "ifconfig -a" and see what network interfaces are recognized.

---

### Post by Auto|MaG on 2005-12-08
lsmod | grep ath only returns 

ath_hal       148432  0

modprobe ath_pci gives

FATAL: Module ath_pci not found

and ifconfig -a lists eth0, lo, and sit0

---

