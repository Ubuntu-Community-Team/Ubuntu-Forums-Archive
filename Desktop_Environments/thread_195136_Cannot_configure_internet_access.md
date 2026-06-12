---
title: "Cannot configure internet access"
date: 2006-06-12
forum: Desktop Environments
---

### Post by aldegaz on 2006-06-12
First of all, before posting here, I have tried to search and manage to solve this problem on my own, even though I am a new user to Ubuntu so I really need the help.
I have a Gateway 7330GZ Laptop with Ubuntu 6.06 installed (I dont have windows and dont have a way to get back).

My LAN connection, as well as my wireless connection are not working. My chipset for my wireless card is the Broadcom chipset, wich in some threads they say some how to's dont work for me:
Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) 

I have installed ndiswrapper, I have installed my drivers succesfully (ndiswrapper -l gives me a "driver present" line.

My Network Settings show me I have a Wireless Connection (eth1), when I set it to "active" it shows a "disconnected" state.

When I choose my Ethernet connection (eth0), it gives me an "idle" connection without any internet connection.

I dont use WEP or WAP and the settings for all the connections are DHCP. I have also tried to set it up as a static IP, but then again, I would not be able to connect.

Now, since I dont have the option to get to Windows I need the internet connection because I work with this laptop, and since it worked fine on an older compaq, I went ahead and installed the latest UBUNTU distro.

If someone, could "step by step" guide me trough a solution, I am sure this thread will help a lot of other people like me.

Thanks

---

### Post by Dr. Nick on 2006-06-12
Just saw your edit to this thread, ill repost it here

Just a few tips, If you get the driver/hardware present on ndiswrapper -l then do 

sudo modprobe ndiswrapper

Also disable any on board ethernet or modem, even if you are not using them. This can be done from system - administration -network. While thier make sure your wireless shows up and is activated. I would reccomend disabling any wep in the router until you get it working.

Also make sure no modules are loaded for you wireles other than ndiswrapper, try "lsmod" and see if you see anything on your wireless card, look for ndiswrapper and see if anything is next to it. You may have to remove another module for ndiswrapper to work. To do that use

sudo modprobe -r *module*

To get ndiswrapper on boot add "ndiswrapper" to /etc/modules.

hopefully one of them will get you further

I see that you have a broadcom, it may have builtin drivers that need to be removed, look for broadcom in the lsmod, I dont have a boradcom so dont know the specific names it would be.

---

### Post by aldegaz on 2006-06-12
Thanks

Like I said, I dont have any WEP or WAP.

When I "ndiswrapper -l" it gives me a "driver present" but it doesnt say anything else like "hardware present".

I have done the sudo modprobe ndiswrapper already with no results

When I go to system/administration/networking it shows my wireless conncection is not active, I then activate it (it takes a while) but still nothing happens.

"lsmod" gives me "ndiswrapper 177364 - used by: 0

I dont have a file "modules" in "etc". Although ndiswrapper is in "etc".

And finally I dont have "broadcom" when I do "lsmod"

---

### Post by Zygzak on 2006-06-12
[QUOTE=aldegaz]
When I "ndiswrapper -l" it gives me a "driver present" but it doesnt say anything else like "hardware present".[/quote]
Bad *.inf file - maybe for wrong card?

---

### Post by aldegaz on 2006-06-12
I dont think so because I got the drivers from [www.gateway.com](www.gateway.com) for my specific laptop. Although I got 2 type of *.inf of files I installed both and then uninstalled the bad one (only 1 was the correct one).
Could it be that Ubuntu is loading a driver and conflicting with what I installed? (seems a lot like windows huh? just joking).

I think the easy way out is to go and buy a pcmcia card? But then again I want to probe people wrong about incompatibility with this OS.

---

### Post by Dr. Nick on 2006-06-12
you could try posting your lsmod output here, someone may see a bad drier loaded.

Also if you can get internet at all, or have the abality to download a deb from another computer their is a program called ndisgtk which will be a gui to ndiswrapper, Its not needed but makes things a tad simpler.

modprobe ndiswrapper wont say anything, just drop you back to a promt.

If you got any drivers cd with the laptop try them drivers, I had better luck using cd included driers as opposed to downloaded ones in my case.

---

### Post by aldegaz on 2006-06-13
Ok, I am going to put lsmod in here. I dont have ANY type of internet connection, so my LAN is not working either.

Is there anyway wich I can install ndisgtk without being online?

I dont have any cd drivers with my laptop.

I am going to type lsmod here because I cant get the information out of my laptop.

Here is lsmod:

ipv6  265600  6
rfcomm 40216  0
l2cap 26244  5 rfcomm
bluetooth 49892  4 rfcomm,l2cap
ppdev 9220  0
i915 20608  1
drm 73236  2 i915
acpi_cpufreq 6792  1
cpufreq_userspace 4696  1
cpufreq_stats 5636  0
freq_table 4740  2 acpi_cpufreq, cpufreq_stats
cpufreq_powersave 1920  0
cpufreq_ondemand 6428  0
cpufreq_conservative 7332  0
video 16260  0
tc1100_wmi 6916 0
sony_acpi 5644  0
pcc_acpi 12416  0
hotkey 11556  0
dev_acpi 11140  0
conatiner 4608 0
button 6672  0
acpi_sbs 19980  0
battery 9988  1 acpi_sbs
i2c_acpi_ec  5120 1 acpi_sbs
i2c_core 21904  1 i2c_acpi_ec
ac 5252 1 acpi_sbs
ndiswrapper 177364  0
af_packet 22920  4
dm_mod 58936  1
md_mod 72532  0
sr_mod 16932  0
sbp2 24196  0
scsi_mod 139496  2 sr_mod,sbp2
parport_pc 35780  0
pcmcia 40508  0
bcm43xx 124044  0
ieee80211softmac 29696  1 bcm43xx
b44 25740  0
ieee80211 37064  2 bcm43xx, ieee80211softmac
ieee80211_crypt  6272  1 iee80211
joydev 10048  0
mii 5888  1 b44
tsdev 8000 0
yenta_socket 28428  1
rsrc_nonstatic 13440  1 yenta_socket
pcmcia_core 42640  3 pcmcia, yenta_socket, rsrc_nonstatic
snd_intel8x0 33692  1
snd_ac97_codec 92704  1 snd_intel8x0
snd_ac97_bus 2304  1 snd_ac97_codec
snd_pcm_oss 53664  0
snd_mixer_oss  18688 1 snd_pcm_oss
snd_pcm 89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer 25220 1 snd_pcm
snd 55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore 10208  1 snd
snd_page_alloc 10632  2 snd_intel8x0,snd_pcm
shpchp 45632 0
pci_hotplug 29236  1 shpchp
pcspkr  2180  0
psmouse 36228  0
serio_raw 7300  0
rtc 13492  0
intel_agp 22940  1
agpgart 34888  3 drm,intel_agp
evdev 9856  2
ext3 135688  1
jbd 58772  1 ext3
ide_generic 1536  0
ohci1394 35124  0
ieee1394 299832  2 spb2,ohci1394
ehci_hcd 32008  0
uhci_hcd 33680  0
usbcore 129668  4 ndiswrapper,ehci_hcd,uhci_hcd
ide_cd 33028  0
cdrom 38560  2 sr_mod,ide_cd
ide_disk 17664  3
piix 11012  1
generic 5124 0
thermal 13576  0
processor 23360  2 acpi_cpufreq,thermal
fan 4868  0
capability 5000 0
commoncap 7296  1 capability
vga16fb 13704  1
vgastate 10368  1 vga16fb
fbcon 42784  72
tileblit 2816  1 fbcon
font 8320  1 fbcon
bitblit 6272  1 fbcon
softcursor 2304  1 bitblit

---

### Post by Dr. Nick on 2006-06-13
Ah the full lsmod really helps out. Hopefully the time spent typing it will be worth it :)


Ubuntu did indeed load some drivers for your card. I think I have located the modules for your ethernet card and your wireless card in their,

I have highlighted your wireless in red and your wired in green. The names on them are not that helpfull lol, the module for mine was preaty easy to pick out of  a list.

What I would reccomend you to try is run

sudo modporbe -r bcm43xx

That should remove your wireless module temporarily. If you reboot your computer or power cycle you wireless card, or unplug/replug it if possible then this  driver will be loaded right back up.

After removing it then reload ndiswrapper by

sudo modprobe ndiswrapper

After that go back into the network control panel and make sure your ethernet is disabled and make sure your wireless shows up and is activated. You could remove your ethernet module by subsituting b44 for bcm43xx in the above command if you choose. That may be all it takes to get online. Just hit configure on the wireless and go pick the ssid of your router.


If doing that works then it is possible to stop the bcm43xx driver from loading at all so you wont have to do that everytime.


If you want you could research any ways to get the bcm43xx driver to work instead of ndiswraper, or you could just use ndiswrapper.

```

ipv6  265600  6
rfcomm 40216  0
l2cap 26244  5 rfcomm
bluetooth 49892  4 rfcomm,l2cap
ppdev 9220  0
i915 20608  1
drm 73236  2 i915
acpi_cpufreq 6792  1
cpufreq_userspace 4696  1
cpufreq_stats 5636  0
freq_table 4740  2 acpi_cpufreq, cpufreq_stats
cpufreq_powersave 1920  0
cpufreq_ondemand 6428  0
cpufreq_conservative 7332  0
video 16260  0
tc1100_wmi 6916 0
sony_acpi 5644  0
pcc_acpi 12416  0
hotkey 11556  0
dev_acpi 11140  0
conatiner 4608 0
button 6672  0
acpi_sbs 19980  0
battery 9988  1 acpi_sbs
i2c_acpi_ec  5120 1 acpi_sbs
i2c_core 21904  1 i2c_acpi_ec
ac 5252 1 acpi_sbs
ndiswrapper 177364  0
af_packet 22920  4
dm_mod 58936  1
md_mod 72532  0
sr_mod 16932  0
sbp2 24196  0
scsi_mod 139496  2 sr_mod,sbp2
parport_pc 35780  0
pcmcia 40508  0
[COLOR=Red] bcm43xx 124044  0[/COLOR]
ieee80211softmac 29696  1 bcm43xx
[COLOR=SeaGreen] b44 25740  0[/COLOR]
ieee80211 37064  2 bcm43xx, ieee80211softmac
ieee80211_crypt  6272  1 iee80211
joydev 10048  0
mii 5888  1 b44
tsdev 8000 0
yenta_socket 28428  1
rsrc_nonstatic 13440  1 yenta_socket
pcmcia_core 42640  3 pcmcia, yenta_socket, rsrc_nonstatic
snd_intel8x0 33692  1
snd_ac97_codec 92704  1 snd_intel8x0
snd_ac97_bus 2304  1 snd_ac97_codec
snd_pcm_oss 53664  0
snd_mixer_oss  18688 1 snd_pcm_oss
snd_pcm 89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer 25220 1 snd_pcm
snd 55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_  oss,snd_pcm,snd_timer
soundcore 10208  1 snd
snd_page_alloc 10632  2 snd_intel8x0,snd_pcm
shpchp 45632 0
pci_hotplug 29236  1 shpchp
pcspkr  2180  0
psmouse 36228  0
serio_raw 7300  0
rtc 13492  0
intel_agp 22940  1
agpgart 34888  3 drm,intel_agp
evdev 9856  2
ext3 135688  1
jbd 58772  1 ext3
ide_generic 1536  0
ohci1394 35124  0
ieee1394 299832  2 spb2,ohci1394
ehci_hcd 32008  0
uhci_hcd 33680  0
usbcore 129668  4 ndiswrapper,ehci_hcd,uhci_hcd
ide_cd 33028  0
cdrom 38560  2 sr_mod,ide_cd
ide_disk 17664  3
piix 11012  1
generic 5124 0
thermal 13576  0
processor 23360  2 acpi_cpufreq,thermal
fan 4868  0
capability 5000 0
commoncap 7296  1 capability
vga16fb 13704  1
vgastate 10368  1 vga16fb
fbcon 42784  72
tileblit 2816  1 fbcon
font 8320  1 fbcon
bitblit 6272  1 fbcon
softcursor 2304  1 bitblit
``` 

If that doesnt work and you want to try ndisgtk then look here
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fn%2Fndisgtk%2Fndisgtk_0.6-0ubuntu1_all.deb&md5sum=820f3a749abd2cb2d097c362103cd07e&arch=all&type=main]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fn%2Fndisgtk%2Fndisgtk_0.6-0ubuntu1_all.deb&md5sum=820f3a749abd2cb2d097c362103cd07e&arch=all&type=main")

Pick a mirror site on a computer with internet then put the deb on a disk or memory stick and transfer it to your ubuntu and install, It may have some unmet dependencies that have to be installed first, not sure on that,

---

### Post by aldegaz on 2006-06-13
ok, thanks again, for the help.

as soon as I removed bcm43xx my wireless card was gone from the network windows

I then reloaded ndiswrapper with no effects at all. :(

I have succesfully installed ndisgtk and it shows that the hardware is not present, even though I have the driver installed.

Although it seems a new and interesting way to aproach my problem, and I have moved forward to solve it, I think I am still missing something.

Could it be this? : [In this thread]("http://www.ubuntuforums.org/showthread.php?t=25683&highlight=siocgifflags") it tells me to put 2 files on the desktop "1. Copy the bcmwl5.inf and bcmwl5.sys files to your desktop" Although the bcmwl5.sys **IS NOT A DRIVER **

---

### Post by Dr. Nick on 2006-06-13
if you dont get the hardware present then the drivers are wrong i believe

EDIT

Since your wireless dissaperaed then the module bcm43xx was controlling it, not ndiswrapper. So any drivers you tried before could be correct if you try them now

---

### Post by aldegaz on 2006-06-13
I found some info []("https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx?action=show&redirect=WiFiBroadcomDriver#head-e70dd6b5c57894d32e3eddc4f3e21d7d6d02230f") adn they talked about "bcm43xx-fwcutter" and how it can get the firmware and make it work for Dapper.
But I really dont understand how to install fwcutter. I think I might have a shot with this...

---

### Post by jitesh on 2006-06-14
Make sure you enable universe in you repositries, then is is as simple as

"apt-get install bcm43xx-fwcutter"

Hope it works.

---

### Post by aldegaz on 2006-06-14
can I enable universe in my repositories even if I dont have an internet connection?

---

### Post by Dr. Nick on 2006-06-14
nope, universe is only good with internet, however you may be able to get that package and transfer it over like ndisgtk. 

[here]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fb%2Fbcm43xx-fwcutter%2Fbcm43xx-fwcutter_20060108-6build1_i386.deb&md5sum=a86e66aba8afc1a7ba1c872ae4192a57&arch=i386&type=main")

If you have ubuntu on any other computer they have a search plugin for firefox built in to search and download packages. It directs to here

[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

---

### Post by aldegaz on 2006-06-14
I have follored the instructions [in this how to]("https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx?action=show&redirect=WifiDocs%2FDriver%2FBroadcom43xx"), but do you guys think this is for me? Since I installed..and everything went good, until trying to unpack the firmwares wich I couldnt (it gave me an error message) I went to the "Problems" part of the "how to" And I found that I do have this problem:
1.2.2.2.1. Problems

If your kernel is updated, but the symbolic links are not updated for this new kernel, you may encounter the following message in dmesg:

[4363141.967000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[4363144.826000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

This can be resolved by upgrading to the latest firmware package version, which no longer uses symbolic links. 

Now, I got the firmware from [here]("http://ubuntu.cafuego.net/pool/dapper-cafuego/bcm43xx/") and this is supposed to be the latest

Oh GOD - will I ever find a solution other than buying a wireless card?

any ideas?

---

### Post by aldegaz on 2006-06-15
*UPDATE*

I have 2 people that have configured SUCCESFULLY their wireless card with a laptop the exact same model as mine (Gateway 7330gz) and Broadcom Corp. Card.

They told me they followed the "how to" for the wireless setup for Broadcom users, and using ndiswrapper.

I think the only difference is that they did have a wired internet access, and they had 5.10 installed and not 6.06

What am I missing? Is there something I should have installed?

If I have to install 5.10 I can do it, I have the Install CD.

What do you guys think?

---

### Post by Dr. Nick on 2006-06-15
you could try 5.10; you never know, I would imagine wired access helps alot since you can easily download and install new packages instead of having to move them between computers.

You could ask the person who got it with ndiswrapper what drivers he used and where from. Without a connection I would think ndiswrapper would be eaisier to get going then the other. If you try ndiswrapper just remember to remove the bcwxx module before starting

---

### Post by Dr. Nick on 2006-06-18
another possibility, I was looking at my wireless setup and found that after removing the native module for my card using modprobe -r that ndiswrapper still would not work until I ran 

sudo modprobe -r ndiswrapper 

followed by

sudo modprobe ndiswrapper

Not sure if that would help you, its just a observation

---

