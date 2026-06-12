---
title: "Memory speed mismatch Ubuntu 20.04"
date: 2021-01-25
forum: Desktop Environments
---

### Post by deepakdeshp on 2021-01-25
[COLOR=#333333][FONT=&amp]My memory speed is 1600MT/S and configured speed is 800 MTS. Is there a way to configure it to 1600 MT/S?

```
  [/FONT][/COLOR]sudo dmidecode --type 17[sudo] password for uma:    
# dmidecode 3.2
Getting SMBIOS data from sysfs.
SMBIOS 2.8 present.


Handle 0x0011, DMI type 17, 40 bytes
Memory Device
	Array Handle: 0x0010
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 4096 MB
	Form Factor: SODIMM
	Set: None
	Locator: Bottom
	Bank Locator: CHANNEL A
	Type: DDR3
	Type Detail: Synchronous Unbuffered (Unregistered)
	Speed: 1600 MT/s
	Manufacturer: Kingston
	Serial Number: 0A10D4E7
	Asset Tag: Asset Tag: 
	Part Number: 99U5469-045.A00LF 
	Rank: 1
	Configured Memory Speed: 800 MT/s
	Minimum Voltage: Unknown
	Maximum Voltage: Unknown
	Configured Voltage: Unknown


Handle 0x0014, DMI type 17, 40 bytes
Memory Device
	Array Handle: 0x0010
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 4096 MB
	Form Factor: SODIMM
	Set: None
	Locator: Top
	Bank Locator: CHANNEL A
	Type: DDR3
	Type Detail: Synchronous Unbuffered (Unregistered)
	Speed: 1600 MT/s
	Manufacturer: Hynix
	Serial Number: 274D41CC
	Asset Tag: Asset Tag: 
	Part Number: HMT451S6BFR8A-PB  
	Rank: 1
	Configured Memory Speed: 800 MT/s
	Minimum Voltage: Unknown
	Maximum Voltage: Unknown
	Configured Voltage: Unknown


uma@mint-18-uma ~ $ sudo dmidecode --type 17|grep -i speed
	Speed: 1600 MT/s
	Configured Memory Speed: 800 MT/s
	Speed: 1600 MT/s
	Configured Memory Speed: 800 MT/s


[COLOR=#333333][FONT=&amp]
```
[/FONT][/COLOR][COLOR=#333333][FONT=&amp]


[/FONT][/COLOR]

---

### Post by deepakdeshp on 2021-01-25
[SIZE=3]Its a 5.5 years old HP laptop

[/SIZE][COLOR=#333333][FONT=&quot][SIZE=3] I upgraded the BIOS in 2019. It is the latest.
I checked the BIOS settings, yet there is nothing to configure memory.
Model 15-afQ01AX
Product M4Y77PA#ACJ[/SIZE][/FONT][/COLOR]

---

### Post by deepakdeshp on 2021-01-27
Bump . Anybody?

---

### Post by ActionParsnip on 2021-01-27
[https://www.phoronix.com/forums/forum/hardware/processors-memory/21788-re-setting-ram-clock-speed](https://www.phoronix.com/forums/forum/hardware/processors-memory/21788-re-setting-ram-clock-speed)

Check RAM speed settings in BIOS

---

### Post by TheFu on 2021-01-27
^^^^^^ this.

Memory speed is controlled by the BIOS. Complain to HP.

---

