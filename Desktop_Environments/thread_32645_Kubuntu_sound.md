---
title: "Kubuntu sound"
date: 2005-05-08
forum: Desktop Environments
---

### Post by ted on 2005-05-08
I am new to linux, less than a week. I have tried Ubuntu, xandros, and Kubuntu. I really like the way kubuntu feels and would like to stick with it, but I am having a few problems. I will only ask one at a time so I don't get overwhelmed. My main concern right now is that I have no sound! I had sound in windows and in xandros, but I never was able to get sound in ubuntu either, that is why I tried kubuntu. If anyone could help I sure would appreciate it.

---

### Post by Xian on 2005-05-08
In Kubuntu try and run the kmix application by clicking the KDE menu icon and choosing the run command selection. Just type in 'kmix' [no quotes] and click okay or go. It should then appear as a speaker icon in your main panel. Can you open it and adjust the mixer settings or it is crossed out and not functional?

---

### Post by ted on 2005-05-08
Thank you for your help. I was able to open kmix and get all of the volume controls. I turned them all up and tried to play a cd using Kscd, I can see the cd playing, but still no sound. What should I try next?

---

### Post by Xian on 2005-05-08
[QUOTE=ted]Thank you for your help. I was able to open kmix and get all of the volume controls. I turned them all up and tried to play a cd using Kscd, I can see the cd playing, but still no sound. What should I try next?[/QUOTE]
Okay, that is a totally separate issue. Kscd AFAIK will only issue sound if your card is hardwired in your tower to the proper components. This is usually not the case with a lot of puters so most people just use other media players instead of making hardware adjustments. There are several players that will do the trick, but since I've used it extensively I'd recommend that you install Totem. Perhaps others will have more recommendations.

---

### Post by SanderAnt on 2005-05-08
Try the Sound System configuration utility in the Control Center under Sound & Multimedia.

Poke around in there and see if the Enable Sound System is checked in the first tab and poke around on the second tab if you still don't hear any sound.

---

### Post by ted on 2005-05-08
Well I tried to install totem movie player. it shows up as installed in kynaptic and so does totem gstreamer. When I try to open it on the desktop it starts to open then an error comes up stating that it won't start and says no reason. Any ideas? I also have kaffeine, JuK, and amaroK. Will any of these play a CD?

---

### Post by gunnyman on 2005-05-08
Check K mixer again and this time look at the switches  tab.
On some sound cards, a digital output is detected and therefore enabled.  This will usually disable the analog output.  If the digital output radio buton is ticked, turn it off.
That just might fix your problem.
I have to do this on every KDE based linux distro I have ever installed.

---

### Post by dekoi on 2005-05-08
I'm fairly new to the world of Linux myself (though I'm finding it a great world to be in), but I had a similar sound issue in the past with Mandrake 9.0. My initial thought on this problem was that ALSA isn't set up properly. ted, is it [ok] in the bootloader? If ALSA comes up "failed" (in red), that could be the source of the problem. But if that's the case, it'll be up to someone who knows WAY more than I on what to do about it.

---

### Post by Xian on 2005-05-08
On my box totem will play a CD even with the arts system running, which I can tell you is no small task for a sound application running in KDE. I can literally play a CD and still hear all the KDE system sounds. If you can't get totem to start then something is really amiss. Have we even yet established that you have sound at all? I recall us talking about it and when you reported back to let me know you were trying to play a CD I figured we were off to the next step. However, if this is not the case then the overall sound issue needs to be resolved before anything else is tackled.

---

### Post by ted on 2005-05-09
I checked that sound system is enabled and it is. In the sound system control center under the hardware tab it is on auto detect. I also saw a place that said test sound, I hit the button and still no sound. Alsa is not coming up as failed when I boot. I am wondering if I have something turned off or if I turned something on by mistake in Kmix. If the buttons are lit does that mean that it is enabled? I hear light popping noises when I toggle the green buttons and when I move the slider for the master volume up and down. Thank you all for being so helpful. I have a feeling it's going to be something so simple I'll laugh, and I did check and make sure the speakers were plugged in and turned on.

---

### Post by improverrr on 2005-05-09
ok, i am surprised that no one has asked this yet going this far into the post.  what kind of sound card is it?  were you able to have sound when your tried xandros linux?  have you happened to have tried a live version CD (of any distro) and had sound?

also, I realize you are trying to play a CD, which must be hard wired like said in past posts, but do you get any sound at all?  like through an .mp3 or rnay other format?

---

### Post by ted on 2005-05-09
I do not have a sound card, I am using the onboard sound. The motherboard is an intel 845gv/ich4. When I was trying out Xandros, sound worked perfectly with absolutly no work needed on my part. I tried to play an mp3, same thing, still no sound.

---

### Post by DrBob on 2005-05-09
Try downloading and compiling the latest version of ALSA ( 1.0.8 ). That got sound working for me (although it is now either choppy, or playing 4x too fast :().

Follow the instructions on [this page](http://www.ubuntulinux.org/wiki/HdaIntelSoundHowto), but you might have to change the driver...

---

### Post by ted on 2005-05-09
I was wondering if any of this information is helpful. I still have no sound, i have not tried to download alsa1.0.8. Maybe some of this information will help someone figure out my sound problem.

2.6.10-5-386
lsmod
Module                  Size  Used by
i915                   18304  1
drm                    59412  2 i915
proc_intf               4100  0
freq_table              4100  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
vga16fb                12488  1
vgastate                8576  1 vga16fb
ipv6                  229504  9
af_packet              20744  2
sd_mod                 16784  0
sis900                 18436  0
snd_intel8x0           29984  1
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  0
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm
hw_random               5524  0
shpchp                 86116  0
pci_hotplug            30512  1 shpchp
ehci_hcd               29444  0
usb_storage            64064  0
usblp                  12032  0
scsi_mod              119936  2 sd_mod,usb_storage
uhci_hcd               30224  0
usbcore               107384  5 ehci_hcd,usb_storage,usblp,uhci_hcd
intel_agp              20636  1
agpgart                31784  3 drm,intel_agp
floppy                 54864  0
pcspkr                  3816  0
rtc                    12216  0
md                     43856  0
evdev                   9088  0
dm_mod                 53116  1
tsdev                   7488  0
capability              5000  0
commoncap               7808  1 capability
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  1 ide_cd
ext3                  120968  1
jbd                    54168  1 ext3
ide_generic             1664  0
piix                    9988  1
ide_disk               18176  3
ide_core              118988  5 usb_storage,ide_cd,ide_generic,piix,ide_disk
unix                   26164  543
thermal                13576  0
processor              22708  1 thermal
fan                     4612  0
fbcon                  34048  71
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  2 vga16fb,vesafb
cfbimgblt               3072  2 vga16fb,vesafb
cfbfillrect             3584  2 vga16fb,vesafb


I hope this info helps. I must say this sound problem is giving me a crash course in Linux and Kubuntu. If anyone has any ideas, let me know them in the simplest terms possible, I've only been using linux a few days (hours). Thanks again for all of your help.

---

