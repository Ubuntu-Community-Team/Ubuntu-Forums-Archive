---
title: "Does not recover from Suspend"
date: 2009-06-12
forum: General Help
---

### Post by riskyayush on 2009-06-12
I am using a Jaunty on my Toshiba Laptop. 

My laptop never comes out of a suspend. When I was using Intrepid, the screen would just stay blank. But with Jaunty, the cursor shows up but nothing happens after that.

On boot up I do get a message : unsupported PM caps version (7).

Can that be the reason for this problem?

Thanx

---

### Post by blueridgedog on 2009-06-12
Based on a search alone, this appears to be common.  Take a look at this bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/342656](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/342656)

Based on Edward's 4/11 post, putting the following script in /etc/pm/sleep.d helped.

```
#!/bin/sh

case $1 in
	hibernate|suspend)
		ifconfig wlan0 down
		modprobe -r rtl8187
   		;;
	thaw|resume)
		modprobe rtl8187
		ifconfig wlan0 up
		;;
	help)
		echo &#8220;$( basename $0 ): Makes wireless play nice with suspend&#8221;
		;;
	*)
		echo &#8220;$( basename $0 ): called wrong&#8221;
		exit 1
		;;
esac
```

If you want to try the script, you can 
```

gksudo gedit /etc/pm/sleep.d/helper.sh
```

Pate in the commands, save, then
```

chmod 755 /etc/pm/sleep.d/helper.sh
```

I called it helper.sh in the above example, but you can call it what you want as all scripts in that directory (I think) will be run on hibernate/thaw/suspend/resume.

---

### Post by riskyayush on 2009-06-12
Thanx a lot for the help.

I did exactly as told. But after I ran the last command I get the error:

chmod: changing permissions of `/etc/pm/sleep.d/helper.sh': Operation not permitted

Is this supposed to happen or am i doing something wrong?

---

### Post by blueridgedog on 2009-06-12
Sorry...add sudo in front of chmod...you are changing the file to be executable.

```
sudo chmod 755 /etc/pm/sleep.d/helper.sh
```

Note that this assumes you have the same module loaded for your wireless...we may need to double check that.

---

### Post by riskyayush on 2009-06-12
Well looks like that code works for rtl8187 wireless card. I have an ar5007eg card and probably that is why it is not working on my laptop. I am not sure if I should mess with the code. So I think I am going to leave it as it is.

---

### Post by blueridgedog on 2009-06-12
Post the output of 

```
sudo lsmod
```

and we can pick the module to change in the script.

Keep in mind, if this fails to work, we can simply delete the file and your system is back to the same state.  There is no real chance of harm.

---

### Post by riskyayush on 2009-06-12
Module                  Size  Used by
i915                   65540  2 
drm                    96296  3 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         435636  5 
arc4                    9856  2 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
ecb                    10752  2 
snd_pcm                82948  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
ath5k                 107008  0 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              217208  1 ath5k
uvcvideo               63240  0 
led_class              12036  1 ath5k
snd                    62628  18 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
compat_ioctl32          9344  1 uvcvideo
iTCO_wdt               19108  0 
psmouse                61972  0 
pcspkr                 10496  0 
cfg80211               38032  2 ath5k,mac80211
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
videodev               41600  1 uvcvideo
iTCO_vendor_support    11652  1 iTCO_wdt
intel_agp              34108  1 
serio_raw              13316  0 
video                  25360  0 
input_polldev          11912  0 
v4l1_compat            21764  2 uvcvideo,videodev
agpgart                42696  3 drm,intel_agp
output                 11008  1 video
usbhid                 42336  0 
usb_storage            82880  0 
r8169                  40836  0 
mii                    13312  1 r8169
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

---

### Post by riskyayush on 2009-06-12
sudo lshw gives me this:

description: Wireless interface
product: AR242x 802.11abg Wireless PCI Express Adapter

---

### Post by blueridgedog on 2009-06-12
It appears that your system is using the ath5k module (driver) which is a better product.  It is unlikely that it is causing the suspend hang, but worth trying. 

Remove 

modprobe -r rtl8187

and replace it with 

modprobe -r ath5k

(using the same gksudo gedit command as before..)

If it fails to solve the problem, you can just delete the file and keep searching.

---

### Post by riskyayush on 2009-07-06
Even after replacing the code suspend/hibernate wont work on my laptop :mad:

---

### Post by andreselsuave on 2009-07-06
try this:

1) Install uswsusp
```
sudo apt-get install uswsusp
```

2)Try suspending:
```
sudo s2ram --force
```

3)Post your results. If they are positive I will help you search in this forum a post which explains how to integrate s2ram in ubuntu native suspend script (so you dont have to type sudo s2ram --force each time u want to suspend, u will be able to use suspend buttons)


EDIT:
Already found that post. It is a complete tutorial on howto fix suspending problems, u should check this out:
[http://ubuntuforums.org/showthread.php?t=471855]("http://ubuntuforums.org/showthread.php?t=471855")

---

### Post by riskyayush on 2009-07-06
I have seen that thread and done as it says. It does not work

---

