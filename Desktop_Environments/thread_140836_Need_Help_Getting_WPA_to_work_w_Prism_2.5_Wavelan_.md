---
title: "Need Help Getting WPA to work w/ Prism 2.5 Wavelan chipset"
date: 2006-03-07
forum: Desktop Environments
---

### Post by neilp85 on 2006-03-07
I've been working for the past couple hours trying to setup wireless connectivity on my laptop with some success.  This is what I've got to work with:

0000:00:09.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
        Subsystem: AMBIT Microsystem Corp.: Unknown device 0200
        Flags: medium devsel, IRQ 10
        Memory at d000a000 (32-bit, prefetchable) [size=4K]
        Capabilities: <available only to root>

So far I've managed to get it to connect to open wireless networks but I'm having problems setting it up to connect to WPA encrypted ones.  I have been following the WPAHowto wiki on using wpa_supplicant.  I'm pretty confident I've set everything correctly in wpa_supplicant.conf but I'll post it here just in case (w/ pswds omitted):


ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

network={
        ssid="Ragnarok"
	proto=WPA
	key_mgmt=WPA-PSK
        #psk="**************"
        psk=************************************************************
}


I then run into problems when I do the test to see if all is well:


$ sudo wpa_supplicant -ieth0 -c/etc/wpa_supplicant.conf -Dhostap -w

ioctl[SIOCSIWPMKSA]: Operation not supported
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
ioctl[SIOCSIWSCAN]: Operation not supported
Failed to initiate AP scan.
ioctl[SIOCGIWSCAN]: Operation not supported
ioctl[SIOCSIWSCAN]: Operation not supported
Failed to initiate AP scan.
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
ioctl[SIOCSIWAP]: Operation not supported

Any help on how to get this working would be great.

---

### Post by neilp85 on 2006-03-08
Has anyone had any luck with this card or one using the same chipset?  I would like to know if continued efforts are worthwhile.

---

