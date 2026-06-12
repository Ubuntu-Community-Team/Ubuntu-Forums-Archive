---
title: "Broadcom BCM4313 Wireless Sometimes doesn't Work on Startup [Ubuntu 11.04 64 bit]"
date: 2011-06-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jsgosselin on 2011-06-15
Hello,

I have a Dell Inspiron 14R installed with Ubuntu 11.04 64bit Natty upgraded from a fresh install of Ubuntu 10.10 Maverick.

My Wlan0 is a Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01). I'm using the Broadcom STA wireless driver version 2.6.38-10-generic and it works well.

However, _sometimes_ on startup (~30% to 100% of the times), Network-Manager doesn't show any wireless network (although there is undoubtedly some). As a workaround, I Suspend/Resume. This as proven to solve the issue each time, but it is annoying to have to do this almost 50% of the time I open my computer. The problem was not present in Maverick, so it is probably something specific to my setup I've done wrong since then.

Would it be possible to have someone help me to trace back the source of my problem please? This would be greatly appreciated.

Thanks you very much. JS

*******************************

[COLOR="Red"]UPDATE:
The *BCM4313 broadcom* wireless card is compatible either with the open source *brcm80211*  driver directly included in the standard kernel or the proprietary *broadcom-wl* driver that can be installed from the *Additional Drivers* feature in Ubuntu (see [https://wiki.archlinux.org/index.php/Broadcom_wireless](https://wiki.archlinux.org/index.php/Broadcom_wireless) and [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) for more informations). As explained in my OP statement, my wireless was not initiating properly on startup for whatever reason.

As a workaround, I first blacklisted the *wl* and *brcm80211* modules and all their dependencies.
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
and added
```
blacklist mac80211
blacklist brcm80211
blacklist cfg80211
blacklist wl
blacklist lib80211_crypt_tkip
blacklist lib80211
```
after that I edited the rc.local file:
```
sudo gedit /etc/rc.local
```
and added, above *exit 0*
```
modprobe brcm80211
```
This way the module associated with the *brcm80211* driver is loaded at the end of the boot process. If I would have liked to use the proprietary *broadcom-wl* instead, I would have *modprobe wl* instead of *modprobe brcm80211*.
[/COLOR]

---

### Post by chili555 on 2011-06-15
When it boots and no networks are showing, please see if the module wl is loaded. Please open a terminal and run:```
lsmod | grep wl
```If it is not loaded, meaning the terminal command comes back blank, load it:```
sudo modprobe wl
```Now does your wireless work? If so, we'll make a quick change to make it persistent.

---

### Post by jsgosselin on 2011-06-15
First, thank you big time for your help chili555.

When it boots and no networks are showing, the module wl seems to be loaded:
```
lsmod | grep wl
wl                   2568244  0 
lib80211               14991  1 wl

```
and
```
sudo modprobe wl
sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

```
Here are some additional informations:
```
sudo iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

```
```
rfkill list
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```
```
sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 68:a3:c4:2e:f0:b0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcm80211 driverversion=2.6.38-10-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0500000-f0503fff
  *-network
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: c1
       serial: 14:fe:b5:9c:69:e7
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:f0400000-f043ffff ioport:2000(size=128)
```

---

### Post by silex89 on 2011-06-15
Do not forget to run "depmod -a" (without the quotes) to resolve the dependencies for the modules.

---

### Post by jsgosselin on 2011-06-15
@silex89
Thanks for your comment I ran "sudo depmod -a" but was able to reproduce the issue afterward after 2 reboots.

Here is more information that maybe will help you guys to understand why I'm experiencing this strange behavior. I ran "lsmod" when no network were showing. Here are the results:
```
lsmod
Module                  Size  Used by
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
rfcomm                 47694  8 
sco                    18187  2 
bnep                   18308  2 
l2cap                  53570  16 rfcomm,bnep
snd_hda_codec_hdmi     28167  1 
snd_hda_codec_realtek   336771  1 
btusb                  18600  2 
bluetooth              72320  9 rfcomm,sco,bnep,l2cap,btusb
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
wl                   2568244  0 
snd_seq_midi           13324  0 
lib80211               14991  1 wl
snd_rawmidi            30486  1 snd_seq_midi
arc4                   12529  2 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
dell_wmi               12681  0 
sparse_keymap          13898  1 dell_wmi
i915                  510478  8 
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               72195  0 
dell_laptop            13827  0 
dcdbas                 14438  1 dell_laptop
joydev                 17606  0 
brcm80211             748941  0 
mac80211              294370  1 brcm80211
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
psmouse                73535  0 
intel_ips              18097  0 
drm_kms_helper         42136  1 i915
serio_raw              13166  0 
cfg80211              178528  2 brcm80211,mac80211
soundcore              12680  1 snd
acpi_igd_opregion      13805  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm                   227495  5 i915,drm_kms_helper,acpi_igd_opregion
i2c_algo_bit           13400  1 i915
video                  19438  1 i915
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
usb_storage            53538  0 
uas                    17996  0 
ahci                   25951  2 
libahci                26642  1 ahci
atl1c                  41171  0 
```
Ok. Then, I suspended/resumed my computer and ran the "lsmod" command again. The output was exactly the same. After I selected my home wireless network in NW and after my system connected to it, 3 lines were added at the beginning of the output :
```
cryptd                 20510  0 
aes_x86_64             17208  1 
aes_generic            38279  1 aes_x86_64
```

I will see if the output of "lsmod" is the same on a successful startup of my wireless system. I think this issue may comes from the sequence from which the module are called at startup. Sometimes the sequence is correct, sometimes it is not.

---

### Post by chili555 on 2011-06-15
What does this tell us about your Broadcom?```
lspci -nn
```I wonder if brcm80211 is correct and wl is *in*correct for your device? If wl is incorrect, we'll remove bcmwl-kernel-source.

Warning! If you are not quite sure, do nothing till you hear from me, as the man said: [http://en.wikipedia.org/wiki/Do_nothing_till_you_hear_from_me](http://en.wikipedia.org/wiki/Do_nothing_till_you_hear_from_me)

You might test by removing temporarily wl:```
sudo rmmod -f wl
```Does your wireless spring to life?

---

### Post by jsgosselin on 2011-06-16
Here are my card's specs:
```
lspci -vvnn | grep 14e4
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

```
lol,concerning your comment on *wl* versus *brcm80211*, that was quite funny. Ok, following your line of thoughts, I blacklisted (in /etc/modprobe.d/blacklist.conf) *b43* *ssb* and *wl* and rebooted.

The problem still occurred, but after a suspend/resume, I was able to connect flawlessly to my wireless connection as I expected with the *brcm80211* driver. Also, I tried to blacklist *brcm80211* (with *wl* free) and I rebooted. Same problem but after a suspend/resume, wireless network was working flawlessly with the *wl* driver (as seen by doing the "lshw -C network"). This means that my card is able to run either with the *wl* or the *brcm80211* driver.

Thus, my guess is that my problem comes from the modules' initialization sequence at startup. There is a module that must be started before another one somewhere in the sequence for my wireless to work. This is probably why it is always working when I come back from suspend; the module that was not loaded soon enough on startup is now already loaded on resume and then, the wireless can initiate. This would also explain why, sometimes, everything works fine directly on the startup.

I've changed things in "Startup Application" a while back. Maybe its what initiated the problem in the first place...but well...I can't say for sure.

It's getting late, I will continue to investigate tomorrow. Thank you very much again for your help chili555, this is a lot of fun trying to figure this out with some help.

---

### Post by chili555 on 2011-06-16
wl depends on lib80211. Let's see if we can force loading. ```
sudo gedit /etc/rc.local
```Add two lines above exit 0```
modprobe lib80211
modprobe wl
```Proofread carefully, save and close gedit. Reboot and check lsmod to see if wl and lib80211 are loaded and brcm80211 and mac80211 and cfg80211 are not. If either or both of mac80211 and cfg80211 do load, try blacklisting them.

---

### Post by jsgosselin on 2011-06-17
Okidooki, I've tried it, but the issue still occurred on startup. To be sure, I blacklisted the *mac80211*, *brcm80211* and *cfg80211* modules before rebooting. *wl* and *lib80211* were both loaded correctly it seems. Had to suspend/resume to make my wireless work as usual. Here is some more information coming from *dmesg* while the problem was occurring (if you could tell me how to use *grep* with multiple subjects, I would be grateful):
```
jsgosselin@jsgosselin-Inspiron-N4010:~$ dmesg | grep eth1
[   20.049478] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.100.82.38
[   37.047448] eth1: no IPv6 routers present
jsgosselin@jsgosselin-Inspiron-N4010:~$ dmesg | grep wl
[   19.782694] wl: module license 'MIXED/Proprietary' taints kernel.
[   19.859296] wl 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.859311] wl 0000:03:00.0: setting latency timer to 64
jsgosselin@jsgosselin-Inspiron-N4010:~$ dmesg | grep lib80211
[   19.778059] lib80211: common routines for IEEE802.11 drivers
[   19.778063] lib80211_crypt: registered algorithm 'NULL'
[   19.956391] lib80211_crypt: registered algorithm 'TKIP'
```
Note that the *wl* driver use *eth1* for my wireless connection. It seems to be a known issue from what I've read on the net.

Also, there is something I should have said to you from the beginning. I'm not using the standard Ubuntu kernel. Instead, I'm using this:
```
uname -a
Linux jsgosselin-Inspiron-N4010 2.6.38-10-generic #44+kamal~mjgbacklight4-Ubuntu SMP Mon Jun 6 19:40:12 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```
This is from [https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight](https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight). I need this in order to be able to control the screen brightness of my computer, which is a feature quite important to me.

However, I've tried your suggestion on a standard kernel I still had installed on my computer,
```
uname -a
Linux jsgosselin-Inspiron-N4010 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011   x86_64 x86_64 x86_64 GNU/Linux
```
,and the same behavior was also present.

I've done a little more research on my issue on the net and I will try to post here a summary of it soon. I think  maybe I will have to recompile the bcmwl driver myself...this idea comes from [https://bbs.archlinux.org/viewtopic.php?pid=923608](https://bbs.archlinux.org/viewtopic.php?pid=923608).

---

### Post by Farharbour on 2011-06-17
I have a Dell  Latitude D610 that will  no longer connect to the  Internet. I have tried  reinstalling network manager but it  simply  does not  work .  I let the  computer  die from lack of  battery poer  once before and the re-installation  restored  the Internet,  but no this is  not working  at all. Does anyone have an  idea how  I might fix this?

---

### Post by jsgosselin on 2011-06-17
Hi Farharbour,
I've seen you've started your own thread ([http://ubuntuforums.org/showthread.php?p=10950557#post109505570](http://ubuntuforums.org/showthread.php?p=10950557#post109505570). I'll post my answer on your thread instead.

---

### Post by jsgosselin on 2011-06-17
Oh yeah, I'm getting somewhere now. Here is what I have done:

I have the latest up-to-date *bmcwl* package installed (version 5.100.82.38+bdcom-0ubuntu3). I blacklisted those modules in /etc/modprobe.d/blacklist.conf :
```
mac80211
brcm80211
cfg80211
wl
lib80211_crypt_tkip
lib80211
```
Then, I rebooted. As expected, I had no wireless on startup since all the modules were not loaded since they where blacklisted.

Then, I loaded the *wl* module and its dependencies:
```
sudo modprobe lib80211
sudo modprobe lib80211_crypt_tkip 
sudo modprobe wl
```
And bam!, I had my wireless working without having to suspend/resume. I've played around with this a little and it seems to be a systematic behavior. [S][COLOR="Red"]In other words, for my wireless to boot on startup, Network Manager needs to be started before the *wl* modules and friends are getting loaded. I can reproduce a similar behavior by playing around with:[/COLOR][/S]
```
[S][COLOR="Red"]sudo stop network-manager
sudo start network-manager[/COLOR][/S]
```

So now the question is, what should I do next?

---

### Post by chili555 on 2011-06-17
I can offer a possibility. I believe NM is started and running before rc.local runs. Please do:```
sudo gedit /etc/rc.local
```Add this above exit 0:```
rmmod -f wl
rmmod -f lib80211
rmmod -f lib80211_crypt_tkip 
sleep 10
modprobe wl
modprobe lib80211
modprobe lib80211_crypt_tkip 
```Proofread, save and close gedit. Reboot and let us have your report.

---

### Post by jsgosselin on 2011-06-17
Ok, first, I was wrong with the assumption that the modules must be loaded after that Network Manager was started. It doesn't seems to be related, not in a way that I can prove yet anyway. Thereby, the workaround proposed by chili555 related to this on post#13 do not work.

However, still, by blacklisting everything related to both *wl* and *brcm80211* drivers as stated in post#12 and by manually loading either *wl* or *brcm80211* on a terminal with *modprobe*, my wireless network initiate correctly systematically.

Also, I have noticed that when I boot with brcm80211 not blacklisted, dmesg will display endlessly the 2 following lines until I suspend/resume:
```
[   42.756165] wl0: fifo 0: descriptor error
[   42.756170] wl0: fatal error, reinitializing
```
The only reference I found on the net related to this was: [https://bbs.archlinux.org/viewtopic.php?pid=923608](https://bbs.archlinux.org/viewtopic.php?pid=923608).

---

### Post by chili555 on 2011-06-17
> However, still, by blacklisting everything related to both wl and brcm80211 drivers as stated in post#12 and by manually loading either wl or brcm80211 on a terminal with modprobe, my wireless network initiate correctly systematically.Then I would try amending my rc.local to:```
modprobe wl
```Leave exit 0 in place; leave everything blacklisted and let rc.local load wl at the end of the boot process.

---

### Post by jsgosselin on 2011-06-17
...and this is a SUCCESS!!! hahahahha =D>

Got my wireless initiated successfully 4 times in a row with *brcm80211* driver directly on startup.

I dis-installed the *bmcwl* package also since I do not really needs it and *brcm80211* seems to run smoother than *wl*

oh yeah, oh nice. Thank you big time chili555 for your help. Will mark this as solved...even though I still do not understand why it's doing this or if its a bug or something. But I'm satisfied with this workaround.

---

### Post by chili555 on 2011-06-17
Awesome! I'm glad it's working by whatever means. Have fun!

---

### Post by Revjohn on 2011-06-29
Thank you!  This was exactly my problem as well (or at least as close as I could come to it... using same Dell, same wireless card (using 32 bit, instead of 64 bit), but all this thread seems to have helped!

Will see if it continues (fingers crossed).  

But thank you!

John

---

### Post by jsgosselin on 2011-07-05
Hey,

Thank you for your comment and I'm happy it may have help you out. For my part, my problem seems under control with this little workaround; wireless is starting flawlessly on each startup.

JS

---

### Post by Revjohn on 2011-07-12
Just stopping by to say that my wireless has been working great since I tried this... every single time I start up.  Which is a fantastic feeling!

Thanks again.  And not only does it work, but I learned a lot about Linux start up, and all that Jazz... enjoyable in its own right!

John

---

### Post by ramkumarh on 2011-08-23
This is brilliant thanks to jsgosselin for starting this and chili555 for helping.

Summarizing the steps here for naive users like me:

sudo vim /etc/modprobe.d/blacklist.conf

and add the following lines and save.

```
blacklist mac80211
blacklist brcm80211
blacklist cfg80211
blacklist wl
blacklist lib80211_crypt_tkip
blacklist lib80211
```


sudo vim /etc/rc.local

and add the following line before "exit 0" line in the file and save.

```
modprobe wl
```

Restart ubuntu!!

---

### Post by nisarg127 on 2011-09-24
> **ramkumarh said:**
> This is brilliant thanks to jsgosselin for starting this and chili555 for helping.

Summarizing the steps here for naive users like me:

sudo vim /etc/modprobe.d/blacklist.conf

and add the following lines and save.

```
blacklist mac80211
blacklist brcm80211
blacklist cfg80211
blacklist wl
blacklist lib80211_crypt_tkip
blacklist lib80211
```
sudo vim /etc/rc.local

and add the following line before "exit 0" line in the file and save.

```
modprobe wl
```Restart ubuntu!!


This helped me to connect to my Wireless Network. However, my system hangs 2/3 times while shutting down. Moreover, if i turn-off my wi-fi and restart it my system hangs.
Any help??

---

### Post by prashastha on 2011-09-29
I am very happy that I found this thread, I have been facing the same problem for nearly 6 months now !! suspend/resume is a great work around and looks like it works every time thanks for this work around. I have still not been able to solve the dependencies can you explain the final solution to me, from what I read it looks like blacklisting the following:

mac80211
brcm80211
cfg80211
wl
lib80211_crypt_tkip
lib80211

and adding 

modprobe wl to /etc/rc.local solved the issue.

Also from linux kernel 2.6.39 onwards the brcm driver has been changed to brcmsmac does this solution apply to the new version of driver as well ?

thanks! 
Prashastha

---

### Post by ramkumarh on 2011-10-27
This problem reappeared with Ubuntu 11.10. And the steps I used above did not solve it. Any help would be appreciated. !!

The "Additional Drivers" utility shows "Broadcom STA wireless driver".. but clicking on "Activate" fails with the following message "Sorry, installation of this driver failed. Please have a look at the log file for details: /var/log/jockey.log "

/var/log/jockey.log had this:
```
2011-10-27 01:26:05,018 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2011-10-27 01:26:05,531 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2011-10-27 01:26:05,634 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2011-10-27 01:26:06,014 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2011-10-27 01:26:06,119 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
```

---

### Post by dyh on 2012-01-09
I am a complete novice, but I had a similar issue, where I could use the Windows Wireless application to install the drivers and wireless would work, but only until the next reboot. I solved the problem by using the "Additional Drivers" utility to deactivate the "Broadcom STA wireless driver".

Good luck!

---

### Post by dyh on 2012-01-09
I spoke to soon. Now the Wireless firmware is missing!

---

### Post by dyh on 2012-01-09
This did the trick:

"My wireless adapter is a Broadcom 802.11b/g BCM4306 and I just had to install the package firmware-b43-installer. It works now! Just simply a sudo apt-get install firmware-b43-installer command."

Source: [http://askubuntu.com/questions/88854/firmware-missing-for-broadcom-802-11b-g-adapter](http://askubuntu.com/questions/88854/firmware-missing-for-broadcom-802-11b-g-adapter)

---

### Post by sportsdude81 on 2012-09-15
> **jsgosselin said:**
> Hello,

I have a Dell Inspiron 14R installed with Ubuntu 11.04 64bit Natty upgraded from a fresh install of Ubuntu 10.10 Maverick.

My Wlan0 is a Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01). I'm using the Broadcom STA wireless driver version 2.6.38-10-generic and it works well.

However, _sometimes_ on startup (~30% to 100% of the times), Network-Manager doesn't show any wireless network (although there is undoubtedly some). As a workaround, I Suspend/Resume. This as proven to solve the issue each time, but it is annoying to have to do this almost 50% of the time I open my computer. The problem was not present in Maverick, so it is probably something specific to my setup I've done wrong since then.

Would it be possible to have someone help me to trace back the source of my problem please? This would be greatly appreciated.

Thanks you very much. JS

*******************************

[COLOR="Red"]UPDATE:
The *BCM4313 broadcom* wireless card is compatible either with the open source *brcm80211*  driver directly included in the standard kernel or the proprietary *broadcom-wl* driver that can be installed from the *Additional Drivers* feature in Ubuntu (see [https://wiki.archlinux.org/index.php/Broadcom_wireless](https://wiki.archlinux.org/index.php/Broadcom_wireless) and [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) for more informations). As explained in my OP statement, my wireless was not initiating properly on startup for whatever reason.

As a workaround, I first blacklisted the *wl* and *brcm80211* modules and all their dependencies.
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
and added
```
blacklist mac80211
blacklist brcm80211
blacklist cfg80211
blacklist wl
blacklist lib80211_crypt_tkip
blacklist lib80211
```
after that I edited the rc.local file:
```
sudo gedit /etc/rc.local
```
and added, above *exit 0*
```
modprobe brcm80211
```
This way the module associated with the *brcm80211* driver is loaded at the end of the boot process. If I would have liked to use the proprietary *broadcom-wl* instead, I would have *modprobe wl* instead of *modprobe brcm80211*.
[/COLOR]


This worked for me on my HP folio 13 except I used this in my rc.local
```

modprobe wl

```

Thanks so much

---

### Post by sportsdude81 on 2012-09-15
> **jsgosselin said:**
> Okidooki, I've tried it, but the issue still occurred on startup. To be sure, I blacklisted the *mac80211*, *brcm80211* and *cfg80211* modules before rebooting. *wl* and *lib80211* were both loaded correctly it seems. Had to suspend/resume to make my wireless work as usual. Here is some more information coming from *dmesg* while the problem was occurring (if you could tell me how to use *grep* with multiple subjects, I would be grateful):
```
jsgosselin@jsgosselin-Inspiron-N4010:~$ dmesg | grep eth1
[   20.049478] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.100.82.38
[   37.047448] eth1: no IPv6 routers present
jsgosselin@jsgosselin-Inspiron-N4010:~$ dmesg | grep wl
[   19.782694] wl: module license 'MIXED/Proprietary' taints kernel.
[   19.859296] wl 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.859311] wl 0000:03:00.0: setting latency timer to 64
jsgosselin@jsgosselin-Inspiron-N4010:~$ dmesg | grep lib80211
[   19.778059] lib80211: common routines for IEEE802.11 drivers
[   19.778063] lib80211_crypt: registered algorithm 'NULL'
[   19.956391] lib80211_crypt: registered algorithm 'TKIP'
```
Note that the *wl* driver use *eth1* for my wireless connection. It seems to be a known issue from what I've read on the net.

Also, there is something I should have said to you from the beginning. I'm not using the standard Ubuntu kernel. Instead, I'm using this:
```
uname -a
Linux jsgosselin-Inspiron-N4010 2.6.38-10-generic #44+kamal~mjgbacklight4-Ubuntu SMP Mon Jun 6 19:40:12 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```
This is from [https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight](https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight). I need this in order to be able to control the screen brightness of my computer, which is a feature quite important to me.

However, I've tried your suggestion on a standard kernel I still had installed on my computer,
```
uname -a
Linux jsgosselin-Inspiron-N4010 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011   x86_64 x86_64 x86_64 GNU/Linux
```
,and the same behavior was also present.

I've done a little more research on my issue on the net and I will try to post here a summary of it soon. I think  maybe I will have to recompile the bcmwl driver myself...this idea comes from [https://bbs.archlinux.org/viewtopic.php?pid=923608](https://bbs.archlinux.org/viewtopic.php?pid=923608).

I have an HP folio and my brightness buttons don't work either. Is this what you fixed (not necessarily on an HP folio) with your custom kernel?

---

