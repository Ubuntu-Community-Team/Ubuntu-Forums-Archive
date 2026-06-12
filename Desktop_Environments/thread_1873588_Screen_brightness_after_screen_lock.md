---
title: "Screen brightness after screen lock"
date: 2011-11-01
forum: Desktop Environments
---

### Post by dave0109 on 2011-11-01
I've been having an intermittent problem with the screen brightness on a Dell Latitude D620.  Ordinarily the brightness is fine and I can control it with the keyboard function keys, without problem.

Then, sometimes after the screen has been locked and I've entered my password, the screen has minimal brightness and the function keys no longer do anything.

However, it's not everytime after the screen has been locked that the problem occurs.

I had it happen just recently and was able to "fix" it but opening Settings Manager -> Display and reversing the screen.  I let it time-out so that it reverted back to normal and the full brightness returned as did the function keys.

---

### Post by dave0109 on 2011-11-05
Anyone?  This happened again today.  Tis annoying.

---

### Post by dave0109 on 2011-11-19
So within the Power Management settings, there's a brightness setting.  If I set it low, the screen appears to go dimmer than with a higher value (but it never comes back to full brightness).  So I tried setting it to 100%, but when I close the Power Management dialog and then go back to it, the value seems to max out at 80%.  I even set the timeout to "never" dim the screen, but that appears to have no effect.

I tried running xfce4-power-manager in debug mode, but it doesn't log anything when the screen gets dimmed.

If I stop either xfce4-power-manager or xscreensaver then the screen is turned off after a delay and comes back dim.  If I stop both of them, then the screen never goes off.

So something that is common to xfce4-power-manager and xscreensaver has a problem, but I don't know enough about the system to know what is shared by those programs.

Can someone with a clue jump in here please...

---

### Post by markbl on 2011-11-19
I have an old Dell 640m laptop which was having various problems with the brightness controls under ubuntu 11.10, problems which I did not see under 10.10. One of those problems was that my screen dimmed after screen lock. All those problems went away for me after I updated the bios in my laptop (from A04 to A10).

---

### Post by dave0109 on 2011-11-20
Thanks, but although I've now upgraded the BIOS, it still doesn't help.

---

### Post by Toz on 2011-11-20
The next time the problem happens, have a look at **~/.xsession-errors** - maybe some clues in there. Feel free to post the contents back.

Also, what directories do you have in /sys/class/backlight? I hava toshiba directory (because my laptop is a toshiba). In that directory, I have:
```

$ ls /sys/class/backlight/toshiba/
actual_brightness  brightness  max_brightness  subsystem  uevent
bl_power	   device      power	       type

```

For whatever directory you have, it would be interesting to note what the value of the file **actual_brightness** is before and after the problem:
```
$ cat /sys/class/backlight/toshiba/actual_brightness 
7

```

Also, you "should" be able to affect the brightness by echoing a value into the **brightness** file like:
```
echo 7 | sudo tee /sys/class/backlight/toshiba/brightness
```
...just make sure the value is between 0 and:
```
$ cat /sys/class/backlight/toshiba/max_brightness 
7

```

Does echoing a value into the brightness file alter your brightness level?

Also, the results of this command might be helpful (to see what kernel parameters you are using):
```
cat /proc/cmdline
```

---

### Post by dave0109 on 2011-11-21
Thanks, I have the value of 7 as well.  Frustratingly, it hasn't gone wrong at all this evening.

---

### Post by dave0109 on 2011-11-23
OK, very interesting results.  I have two symlinks in the backlight directory...

```

/sys/class/backlight$ ls
dell_backlight  intel_backlight

```

When things are working normally, i.e. after booting up, brightness is at my normal level and the Dell function keys work to control the brightness, then it is the data in the dell_backlight files that changes.  So max_brightness is 7 and the value of brightness and actual_brightness goes up or down with the screen brightness as per my requests.

Then the power manager settings kicked in (which is currently set to switch off the screen after 2 minutes rather than the screensavers 15 minutes, but reduce brightness never).  After wiggling the mouse I had a dark screen.

The settings in dell_backlight had not changed, but the ones in intel_backlight had.  There max_brightness is 624, and the value of brightness and actual_brightness was 0.  Echoing 624 into the brightness file restored the screen back to normal.  Result.  So thanks Toz, it's nice to be getting somewhere.

Question is, what now?  And why do I have two links in backlight?

---

### Post by dave0109 on 2011-11-28
Anyone?  Toz?

I've not been able to work out why the dell directory is affected normally, but the intel one after the power-manager and/or screensaver kicks in.

---

### Post by mobius129a on 2011-11-28
What version of Ubuntu are you running?

---

### Post by Toz on 2011-11-28
> **dave0109 said:**
> OK, very interesting results.  I have two symlinks in the backlight directory...

```

/sys/class/backlight$ ls
dell_backlight  intel_backlight

```

When things are working normally, i.e. after booting up, brightness is at my normal level and the Dell function keys work to control the brightness, then it is the data in the dell_backlight files that changes.  So max_brightness is 7 and the value of brightness and actual_brightness goes up or down with the screen brightness as per my requests.

Then the power manager settings kicked in (which is currently set to switch off the screen after 2 minutes rather than the screensavers 15 minutes, but reduce brightness never).  After wiggling the mouse I had a dark screen.

The settings in dell_backlight had not changed, but the ones in intel_backlight had.  There max_brightness is 624, and the value of brightness and actual_brightness was 0.  Echoing 624 into the brightness file restored the screen back to normal.  Result.  So thanks Toz, it's nice to be getting somewhere.

Question is, what now?  And why do I have two links in backlight?

When this happens, is anything logged to ~/.xsession-errors or /var/log/Xorg.0.log? What kind of video card do you have? Can you post back the contents of /var/log/Xorg.0.log and the results of:
```
lsmod
```
...and
```
cat /proc/cmdline
```

---

### Post by dave0109 on 2011-11-30
@mobuis - Xubuntu 11.10

@Toz - nothing logged to ~/.xsession-errors nor /var/log/Xorg.0.log once the powermanager kicks in.  The latter has the same repeating 3 lines:-

```

[    32.469] (II) intel(0): EDID vendor "SEC", prod id 17495
[    32.469] (II) intel(0): Printing DDC gathered Modelines:
[    32.469] (II) intel(0): Modeline "1440x900"x0.0   95.44  1440 1504 1536 1744  900 903 906 912 -hsync -vsync (54.7 kHz)

```

I've an Intel 945GM Chipset integrated graphics on this laptop.

```

$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.0.0-13-generic root=UUID=cad3e6ac-1c74-4888-b06e-17fe18a448c3 ro quiet splash vt.handoff=7
$ lsmod
Module                  Size  Used by
twofish_generic        16579  0 
twofish_i586           12503  0 
twofish_common         20823  2 twofish_generic,twofish_i586
xts                    12644  0 
gf128mul               14503  1 xts
dm_crypt               22565  0 
snd_hrtimer            12648  1 
bnep                   17923  2 
rfcomm                 38408  4 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               251814  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
snd_hda_codec_idt      60049  1 
joydev                 17393  0 
btusb                  18160  0 
bluetooth             148839  11 bnep,rfcomm,btusb
usbhid                 41905  0 
hid                    77367  1 usbhid
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop
pcmcia                 39822  0 
arc4                   12473  2 
psmouse                73673  0 
snd_hda_intel          24262  3 
snd_hda_codec          91754  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
serio_raw              12990  0 
snd_seq_midi_event     14475  1 snd_seq_midi
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
b43                   318816  0 
i915                  505108  2 
snd_seq                51567  3 snd_seq_midi,snd_seq_midi_event
mac80211              393459  1 b43
snd_timer              28932  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         32889  1 i915
drm                   192226  3 i915,drm_kms_helper
cfg80211              172392  2 b43,mac80211
snd                    55902  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    18744  1 dell_wmi
i2c_algo_bit           13199  1 i915
soundcore              12600  1 snd
video                  18908  1 i915
coretemp               13188  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   132972  0 
ssb                    50682  1 b43

```

---

### Post by Toz on 2011-11-30
What happens if you boot with the kernel parameter **acpi_backlight=vendor**? Try a test using the instructions at: [https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot]("https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot")

---

### Post by dave0109 on 2011-11-30
That didn't appear to have an effect.  Hoping I added the parameter in the right place. It's not something I've done before.  Thanks for sticking with me. :)

```

$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.0.0-13-generic root=UUID=cad3e6ac-1c74-4888-b06e-17fe18a448c3 ro quiet splash vt.handoff=7 acpi_backlight=vendor
$ lsmod
Module                  Size  Used by
snd_hrtimer            12648  1 
bnep                   17923  2 
rfcomm                 38408  12 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               251814  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
snd_hda_codec_idt      60049  1 
joydev                 17393  0 
usbhid                 41905  0 
hid                    77367  1 usbhid
snd_hda_intel          24262  3 
snd_hda_codec          91754  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
btusb                  18160  2 
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
bluetooth             148839  23 bnep,rfcomm,btusb
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_seq_midi           13132  0 
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop
pcmcia                 39822  0 
snd_rawmidi            25241  1 snd_seq_midi
arc4                   12473  2 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  3 snd_seq_midi,snd_seq_midi_event
psmouse                73673  0 
snd_timer              28932  3 snd_hrtimer,snd_pcm,snd_seq
b43                   318816  0 
serio_raw              12990  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              393459  1 b43
snd                    55902  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    18744  1 dell_wmi
i915                  505108  2 
cfg80211              172392  2 b43,mac80211
drm_kms_helper         32889  1 i915
drm                   192226  3 i915,drm_kms_helper
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
coretemp               13188  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   132972  0 
ssb                    50682  1 b43

```

---

### Post by dave0109 on 2011-11-30
There appears to be a small difference, in that now, the power manager doesn't appear to kick in.  I have in the 'On AC' -> Monitor settings:-

Put display to sleep: Never
Switch off display when inactive: 1 minute (good for testing)
Reduce screen brightness: Never

Previously, this would kick in after 1 minute and then not come back at full brightness.

Now, with the kernel boot param, it's not kicking in, and it's the screen saver that's blanking the screen after 5 mins (as set in the screensaver settings).

---

### Post by Toz on 2011-11-30
> **dave0109 said:**
> That didn't appear to have an effect.  Hoping I added the parameter in the right place. It's not something I've done before.  Thanks for sticking with me. :)

```

$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.0.0-13-generic root=UUID=cad3e6ac-1c74-4888-b06e-17fe18a448c3 ro quiet splash vt.handoff=7 acpi_backlight=vendor
$ lsmod
Module                  Size  Used by
snd_hrtimer            12648  1 
bnep                   17923  2 
rfcomm                 38408  12 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               251814  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
snd_hda_codec_idt      60049  1 
joydev                 17393  0 
usbhid                 41905  0 
hid                    77367  1 usbhid
snd_hda_intel          24262  3 
snd_hda_codec          91754  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
btusb                  18160  2 
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
bluetooth             148839  23 bnep,rfcomm,btusb
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_seq_midi           13132  0 
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop
pcmcia                 39822  0 
snd_rawmidi            25241  1 snd_seq_midi
arc4                   12473  2 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  3 snd_seq_midi,snd_seq_midi_event
psmouse                73673  0 
snd_timer              28932  3 snd_hrtimer,snd_pcm,snd_seq
b43                   318816  0 
serio_raw              12990  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              393459  1 b43
snd                    55902  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    18744  1 dell_wmi
i915                  505108  2 
cfg80211              172392  2 b43,mac80211
drm_kms_helper         32889  1 i915
drm                   192226  3 i915,drm_kms_helper
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
coretemp               13188  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   132972  0 
ssb                    50682  1 b43

```

After you've booted with the acpi_backlight=vendor kernel parameter, post back the results of:
```
cat /proc/cmdline
```
...and
```
ls /sys/class/backlight
```
...and
```
ls /proc/acpi
```

---

### Post by Toz on 2011-11-30
> **dave0109 said:**
> There appears to be a small difference, in that now, the power manager doesn't appear to kick in.  I have in the 'On AC' -> Monitor settings:-

Put display to sleep: Never
Switch off display when inactive: 1 minute (good for testing)
Reduce screen brightness: Never

Previously, this would kick in after 1 minute and then not come back at full brightness.

Now, with the kernel boot param, it's not kicking in, and it's the screen saver that's blanking the screen after 5 mins (as set in the screensaver settings).

Is the power manager daemon working?
```
ps -ef | grep power-manager | grep -v grep
```

---

### Post by dave0109 on 2011-12-01
```
cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.0.0-13-generic root=UUID=cad3e6ac-1c74-4888-b06e-17fe18a448c3 ro quiet splash vt.handoff=7 acpi_backlight=vendor

```
...and
```
ls /sys/class/backlight
dell_backlight  intel_backlight

```
...and
```
ls /proc/acpi
ac_adapter  battery  button  event  wakeup
```

> Is the power manager daemon working?
Yeah, it's running.

---

### Post by Toz on 2011-12-01
For some reason you have 2 backlight interfaces and I'm guessing that when you are coming out of screensaver mode, the system is switching between the two. Unfortunately I don't know why.

What happens if you:
```
sudo modprobe -r dell_laptop
```

If its successful, also check your laptop function keys to see if they still work.

---

### Post by dave0109 on 2011-12-02
OK, that has resulted in the removal of dell_backlight from /sys/class/backlight, but it's had no effect.  When power-manager kicks in, blanks the screen and I bring it back, the brightness is still dim.

I'll try booting with the kernel option and then do the module removal too.... which made no difference. :(

---

### Post by dave0109 on 2011-12-03
Looks like a bug in the kernel for the intel 915 driver, which has now been patched and made its way into the next kernel update 3.0.0-14.  Gonna wait for this to get released and see if it fixes the issue.  Should help all the others out there too, no matter which flavour of Ubuntu.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/872652](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/872652)

---

### Post by dave0109 on 2011-12-16
Finally solved with kernel 3.0.0-15-generic.  Number 14 didn't do it on my system, but 15 has, without needing any additional boot parameters.

---

