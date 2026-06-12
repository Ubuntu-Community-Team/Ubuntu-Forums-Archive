---
title: "Unable to get M-Audio Audiophile USB soundcard to work"
date: 2006-01-15
forum: General Help
---

### Post by dabotsonline on 2006-01-15
I have tried the suggestions/tutorials in these threads: [http://www.ubuntuforums.org/showthread.php?t=30891](http://www.ubuntuforums.org/showthread.php?t=30891) , [http://www.ubuntuforums.org/showthread.php?t=59321](http://www.ubuntuforums.org/showthread.php?t=59321) , [http://www.ubuntuforums.org/showthread.php?t=44753](http://www.ubuntuforums.org/showthread.php?t=44753) , [http://www.ubuntuforums.org/showthread.php?t=116737](http://www.ubuntuforums.org/showthread.php?t=116737) , [http://www.ubuntuforums.org/showthread.php?t=76860](http://www.ubuntuforums.org/showthread.php?t=76860) , [http://www.ubuntuforums.org/showthread.php?t=102970](http://www.ubuntuforums.org/showthread.php?t=102970) , [http://www.ubuntuforums.org/showthread.php?t=79959](http://www.ubuntuforums.org/showthread.php?t=79959) , [http://www.ubuntuforums.org/showthread.php?t=113939](http://www.ubuntuforums.org/showthread.php?t=113939) , [http://www.ubuntuforums.org/showthread.php?t=76978](http://www.ubuntuforums.org/showthread.php?t=76978) , [http://www.ubuntuforums.org/showthread.php?t=76978](http://www.ubuntuforums.org/showthread.php?t=76978) , [http://www.ubuntuforums.org/showthread.php?t=101125](http://www.ubuntuforums.org/showthread.php?t=101125) and [http://www.ubuntuforums.org/showthread.php?t=59321](http://www.ubuntuforums.org/showthread.php?t=59321) but I am unable to get any sound at all in any program, either through my soundcard or through my onboard sound (AC97). 

Here is the output of cat /proc/asound/cards: > 0 [SI7012 ]: ICH - SiS SI7012 SiS SI7012 with VT1616i at 0xe200, irq 18 1 [tm ]: USB-Audio - Audiophile USB (tm) M-Audio Audiophile USB (tm) at usb-0000:00:03.1-1, full speed 

and here is the output of lsmod: > Module                  Size  Used by
rfcomm                 34972  0 
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
speedstep_lib           4228  0 
cpufreq_userspace       4444  0 
cpufreq_stats           5124  0 
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0 
cpufreq_ondemand        5916  0 
cpufreq_conservative     6820  0 
pcmcia                 24584  2 
video                  16004  0 
tc1100_wmi              6916  0 
sony_acpi               5516  0 
pcc_acpi               11392  0 
hotkey                  9508  0 
dev_acpi               11396  0 
i2c_acpi_ec             5760  0 
button                  6672  0 
battery                 9604  0 
container               4608  0 
ac                      4996  0 
ipv6                  217408  12 
af_packet              20232  6 
pcspkr                  3652  0 
rtc                    11832  0 
snd_usb_audio          68160  0 
snd_usb_lib            13824  1 snd_usb_audio
snd_rawmidi            22816  1 snd_usb_lib
snd_seq_device          8204  1 snd_rawmidi
snd_hwdep               8608  1 snd_usb_audio
yenta_socket           22540  1 
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_intel8x0           30144  1 
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0 
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  4 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  12 snd_usb_audio,snd_rawmidi,snd_seq_device,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
i2c_sis96x              5252  0 
i2c_core               19728  2 i2c_acpi_ec,i2c_sis96x
pci_hotplug            24628  0 
sis_agp                 8452  1 
agpgart                32328  1 sis_agp
dm_mod                 50364  1 
joydev                  9280  0 
tsdev                   7616  0 
evdev                   9088  1 
psmouse                26116  0 
mousedev               10912  1 
parport_pc             31812  0 
lp                     11460  0 
parport                32072  2 parport_pc,lp
md                     40656  0 
ext3                  115976  1 
jbd                    48536  1 ext3
thermal                13192  0 
processor              23100  1 thermal
fan                     4740  0 
usbhid                 30688  0 
sis900                 19456  0 
mii                     5248  1 sis900
ehci_hcd               29448  0 
ohci_hcd               18564  0 
usbcore               104316  6 snd_usb_audio,snd_usb_lib,usbhid,ehci_hcd,ohci_hcd
ide_cd                 36996  0 
cdrom                  33952  1 ide_cd
ide_disk               16128  3 
ide_generic             1664  0 
sis5513                14472  1 
ide_core              125268  4 ide_cd,ide_disk,ide_generic,sis5513
unix                   24624  415 
vesafb                  8088  0 
capability              5000  0 
commoncap               6784  1 capability
vga16fb                12232  1 
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72 
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon 

Could somebody please tell me, step by step from the beginning, how to get my soundcard working? Thank you, Nick P.S. For some reason, I have recently had to type "sudo dhclient" at the terminal to access the internet. How do I overcome this?

---

### Post by 23meg on 2006-01-15
Is your card listed as a sound device in the apps you're using, or does it not appear at all? Is it listed in System / Preferences / Sounds?

---

### Post by dabotsonline on 2006-01-15
[QUOTE=23meg]Is your card listed as a sound device in the apps you're using, or does it not appear at all?[/quote]
Doesn't appear at all.

> Is it listed in System / Preferences / Sounds?
Do you mean System Settings / Sound & Multimedia / Hardware?  If so, no.

---

### Post by 23meg on 2006-01-15
Sorry, didn't notice you were using KDE. 

Have you been to [this page]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Midiman%2FMAudio&card=Audiophile+USB.&chip=&module=usb-audio")? The info in there seems like it might help.

---

### Post by dabotsonline on 2006-01-15
[QUOTE=23meg]
Have you been to [this page]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Midiman%2FMAudio&card=Audiophile+USB.&chip=&module=usb-audio")? The info in there seems like it might help.[/QUOTE] That doesn't work either 
:???:

---

### Post by dabotsonline on 2006-01-24
Any other suggestions?

---

