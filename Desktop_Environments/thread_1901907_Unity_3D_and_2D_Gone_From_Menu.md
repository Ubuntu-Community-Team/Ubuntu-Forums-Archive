---
title: "Unity 3D and 2D Gone From Menu"
date: 2011-12-29
forum: Desktop Environments
---

### Post by TomAwezome on 2011-12-29
I am currently in a bit of a problem here. I have lost the Unity selections in the login screen. Gnome Classic, Gnome Classic (No Effects) and the recovery console are still there, but all Unity selections are gone. Any tips on how to go about getting it back? (Or, which might help me more, help me figure out what caused it?)

---

### Post by Frogs Hair on 2011-12-29
That's odd you would lose both options . Check the software center and make sure they are installed . If you are not the only user on the computer someone could have removed them . Other than Unity and Unity 2D being removed I don't know what would cause that .

---

### Post by wildmanne39 on 2011-12-29
Hi, did you upgrade your video card driver? install updates or remove anything when this started?

Please post the output of:
```
/usr/lib/nux/unity_support_test 
-p
```
```
lspci | grep VGA
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by TomAwezome on 2011-12-29
Well, I suppose this could be a good sign; I managed to get into Unity 3D via recovery console (I believe by typing "unity --replace") and am posting these outputs via Unity.
At least it appears everything's installed correctly, right?
I do remember fiddling (simply removing then reinstalling) with ubiquity and nautilus (trying to figure out a different bug my PC had)

```
tom@tom-945GC-M4:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945G x86/MMX/SSE2
OpenGL version string:  1.4 Mesa 7.11

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```

```
tom@tom-945GC-M4:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
```

```
tom@tom-945GC-M4:~$ lsmod
Module                  Size  Used by
dm_crypt               22565  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
ppdev                  12849  0 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               251814  3 vboxpci,vboxnetadp,vboxnetflt
snd_usb_audio         100880  0 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_usbmidi_lib        24558  1 snd_usb_audio
snd_hda_codec_realtek   254125  1 
ipt_REJECT             12512  1 
snd_hda_intel          24262  2 
ipt_LOG                12783  4 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  2 snd_usb_audio,snd_hda_codec
xt_limit               12541  6 
xt_tcpudp              12531  16 
snd_pcm                80435  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
xt_addrtype            12596  4 
xt_state               12514  9 
snd_seq_midi           13132  0 
snd_rawmidi            25241  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
parport_pc             32114  1 
ip6table_filter        12711  1 
ip6_tables             22528  1 ip6table_filter
nf_nat_irc             12542  0 
nf_conntrack_irc       13138  1 nf_nat_irc
nf_nat_ftp             12595  0 
nf_nat                 24958  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      19084  11 nf_nat
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
nf_conntrack_ftp       13183  1 nf_nat_ftp
nf_conntrack           70103  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12706  1 
ip_tables              18106  1 iptable_filter
x_tables               21975  10 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
binfmt_misc            17292  1 
snd                    55902  15 snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
usb_storage            44173  0 
uas                    17699  0 
floppy                 60310  0 
i915                  505159  4 
drm_kms_helper         32889  1 i915
drm                   192194  5 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
r8169                  43104  0 
video                  18908  1 i915
zram                   18007  1 

```
From what I know (not very much!) everything looks fine. (Compiz Cube and everything else from ccsm works as well) :-k

---

### Post by wildmanne39 on 2011-12-29
Hi, yes all of that looks good, so you are booted into unity are you having any problems now?
Thanks

---

### Post by TomAwezome on 2011-12-29
> **wildmanne39 said:**
> Hi, yes all of that looks good, so you are booted into unity are you having any problems now?
Thanks

None that I can really see, besides some theme errors. (Which are my fault from fiddling with theme stuff much earlier on)

I'll go ahead and see if, for whatever reason, Unity will decide to appear in the log in menu.

[EDIT] Nope, still no Unity options

---

### Post by wildmanne39 on 2011-12-29
Hi, unity is actually listed as ubuntu.
Thanks

---

### Post by TomAwezome on 2011-12-29
> **wildmanne39 said:**
> Hi, unity is actually listed as ubuntu.
Thanks
Thanks, but all that's in the menu is GNOME, GNOME Classic, Recovery Console, and User Defined Session (User Defined Session leaves me at a black screen, just for the record.)

---

### Post by wildmanne39 on 2011-12-29
Hi, I am not sure, I googled it but I did not find that exact problem, you may have uninstalled something like the ubuntu-desktop that is causing the problem but I would think since you can get to the unity desktop in recovery mode that you did not but I suggest looking at this link it will not hurt to reinstall the ubuntu desktop and check the things on that site.
[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html) 
Thanks

---

### Post by TomAwezome on 2011-12-29
Well, I am just now putting in ```
sudo apt-get install ubuntu-desktop
``` and it appears that ubuntu-desktop was not installed. Installing now! ;)

---

### Post by wildmanne39 on 2011-12-29
Hi, that sure would cause problems.
Thanks

---

### Post by TomAwezome on 2011-12-29
Thank you very much mate! After installing ubuntu-desktop (and also installing desktop-base) both Unity 3D and 2D are now in my menu. Again, I can't thank you enough. :D

[EDIT] Marked as solved. :)

---

### Post by wildmanne39 on 2011-12-29
Hi, your welcome! I am glad it is working.
Enjoy

---

