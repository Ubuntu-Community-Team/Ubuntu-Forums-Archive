---
title: "Inspiron 1525 bluetooth"
date: 2008-11-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mescaleeto on 2008-11-23
Yeah I have an inspiron 1525 that apparently has built in bluetooth. I've gone through a few guides with no luck, has anyone else encountered similar hurdles enabling bluetooth?

---

### Post by superm1 on 2008-11-23
Three things - in this order:

1) Make *sure* the HW switch is enabled in the BIOS and it's flipped on

2) sudo dellWirelessCtrl --sw_bt 1 --bt 1

3) If you have a dual boot, turn it on in windows and reboot

Let us know what works for you.

---

### Post by mescaleeto on 2008-11-24
In BIOS everything appears to be switched on. When I tried 'dellWirelessCtrl' it told me that the command was not found. And I don't dual-boot, which is a little frustrating since the most common remedy seems to be to turn it on in windows :\

---

### Post by superm1 on 2008-11-24
Install libsmbios-bin and you should have the binaries available.

---

### Post by mescaleeto on 2008-11-24
Still nothing, should dellwirelessctrl exist as a package?

---

### Post by superm1 on 2008-11-24
Nope, it's part of libsmbios-bin:

$dpkg -L libsmbios-bin
/.
/usr
/usr/sbin
/usr/sbin/activateCmosToken
/usr/sbin/ascii2enUS_scancode
/usr/sbin/assetTag
/usr/sbin/createUnitTestFiles
/usr/sbin/dellBiosUpdate
/usr/sbin/dellLcdBrightness
/usr/sbin/dellLEDCtl
/usr/sbin/dellMediaDirectCtl
**/usr/sbin/dellWirelessCtl**
/usr/sbin/disable_console_redir
/usr/sbin/dumpCmos
/usr/sbin/dumpSmbios
/usr/sbin/getPasswordFormat
/usr/sbin/getSystemId
/usr/sbin/isCmosTokenActive
/usr/sbin/mkbiospkg.sh
/usr/sbin/probes
/usr/sbin/propertyTag
/usr/sbin/serviceTag
/usr/sbin/smitest
/usr/sbin/stateByteCtl
/usr/sbin/upBootCtl
/usr/sbin/verifySmiPassword
/usr/sbin/wakeupCtl
/usr/share
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/smbios-bin.1.gz
/usr/share/doc
/usr/share/doc/libsmbios-bin
/usr/share/doc/libsmbios-bin/README
/usr/share/doc/libsmbios-bin/copyright
/usr/share/doc/libsmbios-bin/COPYING-OSL.gz
/usr/share/doc/libsmbios-bin/changelog.Debian.gz
/usr/share/man/man1/smitest.1.gz
/usr/share/man/man1/dellWirelessCtl.1.gz
/usr/share/man/man1/ascii2enUS_scancode.1.gz
/usr/share/man/man1/createUnitTestFiles.1.gz
/usr/share/man/man1/dellBiosUpdate.1.gz
/usr/share/man/man1/dellLcdBrightness.1.gz
/usr/share/man/man1/dumpSmbios.1.gz
/usr/share/man/man1/mkbiospkg.sh.1.gz
/usr/share/man/man1/getPasswordFormat.1.gz
/usr/share/man/man1/dumpCmos.1.gz
/usr/share/man/man1/propertyTag.1.gz
/usr/share/man/man1/probes.1.gz
/usr/share/man/man1/getSystemId.1.gz
/usr/share/man/man1/assetTag.1.gz
/usr/share/man/man1/wakeupCtl.1.gz
/usr/share/man/man1/upBootCtl.1.gz
/usr/share/man/man1/stateByteCtl.1.gz
/usr/share/man/man1/activateCmosToken.1.gz
/usr/share/man/man1/verifySmiPassword.1.gz
/usr/share/man/man1/isCmosTokenActive.1.gz
/usr/share/man/man1/serviceTag.1.gz
/usr/share/man/man1/dellLEDCtl.1.gz
/usr/share/man/man1/dellMediaDirectCtl.1.gz
/usr/share/man/man1/disable_console_redir.1.gz


**dellWirelessCtl**

Case is important.

---

### Post by mescaleeto on 2008-11-24
I was typing Ctrl rather than Ctl, oops. When I typed it in correctly it gave me this output 

~$ sudo dellWirelessCtl --sw_bt 1 --bt 1
Wireless Info:
	Hardware switch supported
	Hardware switch is On
	WiFi Locator supported
	Wireless Keyboard not supported
	NVRAM Size: 256 bytes
	NVRAM format version: 1

Radio Status for WLAN:
	WLAN supported
	WLAN installed
	WLAN enabled
	Status Code: 0

Radio Status for Bluetooth:
	Bluetooth supported
	Bluetooth not installed
	Bluetooth enabled
	Status Code: 2

Radio Status for WWAN:
	WWAN supported
	WWAN not installed
	WWAN enabled
	Status Code: 2

Wireless Switch Configuration
	WLAN switch control on
	Bluetooth switch control on
	WWAN switch control on
	switch config not locked
	WiFi locator enabled
	WiFi Locator config not locked

---

### Post by superm1 on 2008-11-24
So according to that, you don't have a bluetooth module installed, or it's seated improperly.

Can you verify that it's on the bus?  lsusb output will show it.  Also, the BIOS should have an indicator whether the hardware is present.

---

### Post by SpreadFirefox on 2008-11-24
Sorry but I have same laptop here is the output:
```
Radio Status for Bluetooth:
        Bluetooth supported
        Bluetooth installed
        Bluetooth enabled
        Status Code: 0

```
I have kdebluetooth4 but it doesn't show interface. May I ask for your suggestions?

---

### Post by superm1 on 2008-11-24
> **SpreadFirefox said:**
> Sorry but I have same laptop here is the output:
```
Radio Status for Bluetooth:
        Bluetooth supported
        Bluetooth installed
        Bluetooth enabled
        Status Code: 0

```I have kdebluetooth4 but it doesn't show interface. May I ask for your suggestions?
kdebluetooth4 is broken for intrepid.  You'll have to revert to bluez-gnome if you want to set up bluetooth.

---

### Post by SpreadFirefox on 2008-11-25
I have used obexftp and obexpush . Works great but I hope soon we will have frontend working for KDE4.

---

