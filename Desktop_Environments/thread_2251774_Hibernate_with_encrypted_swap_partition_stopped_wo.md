---
title: "Hibernate with encrypted swap partition stopped working (it worked before)"
date: 2014-11-06
forum: Desktop Environments
---

### Post by el_baby on 2014-11-06
I configured everything as explained in [EnableHibernateWithEncryptedSwap]("https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap") on a cleanly installed 14.04 dell precision m4600 and it **DID** work for some time.

Since last week, I don't know what changed but the system fails to come back from hibernation.

I get the passphrase field. I fill it in and press enter but the field stays there. I DON'T get the "cryptsetup: cryptswap1 set up successfully" message and the system boots to the login screen. However, if I type "swapon -s" I see the /dev/mapper/cryptswap1 partition enabled and it DOES have enough space for all the RAM (I have 16Gb RAM and the partition is 24Gb).

According to /var/log/pm-suspend the system DOES hibernate - the lines of a hibernate action look like this:

```
Initial commandline parameters: 
Wed Nov  5 15:51:03 ART 2014: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:
/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status hibernate hibernate:
/usr/lib/pm-utils/sleep.d/000record-status hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux dellores 3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
ctr                    13049  2 
ccm                    17773  2 
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               409815  3 vboxnetadp,vboxnetflt,vboxpci
bnep                   19624  2 
nfsd                  280289  2 
rfcomm                 69160  8 
auth_rpcgss            59338  1 nfsd
nfs_acl                12837  1 nfsd
nfs                   236501  0 
lockd                  93977  2 nfs,nfsd
sunrpc                289260  6 nfs,nfsd,auth_rpcgss,lockd,nfs_acl
dm_crypt               23177  1 
binfmt_misc            17468  1 
fscache                63988  1 nfs
uvcvideo               80885  0 
intel_rapl             18773  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
arc4                   12608  2 
iwldvm                232285  0 
i2400m_usb             36521  0 
i2400m                107913  1 i2400m_usb
videodev              134688  2 uvcvideo,videobuf2_core
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
snd_hda_codec_idt      54718  1 
snd_hda_intel          56451  4 
snd_hda_codec         192906  2 snd_hda_codec_idt,snd_hda_intel
mac80211              630653  1 iwldvm
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec,snd_hda_intel
wimax                  34704  1 i2400m
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
coretemp               13435  0 
dell_wmi               12761  0 
dell_laptop            18168  0 
mei_me                 18627  0 
sparse_keymap          13948  1 dell_wmi
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
mei                    82276  1 mei_me
lp                     17759  0 
iwlwifi               169932  1 iwldvm
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
ppdev                  17671  0 
btusb                  32412  0 
kvm_intel             143148  0 
snd                    69322  17 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
kvm                   451729  1 kvm_intel
dcdbas                 14928  1 dell_laptop
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
bluetooth             391136  22 bnep,btusb,rfcomm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
parport_pc             32701  0 
aesni_intel            55624  1755 
parport                42348  3 lp,ppdev,parport_pc
aes_x86_64             17131  1 aesni_intel
joydev                 17381  0 
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
mac_hid                13205  0 
ablk_helper            13597  1 aesni_intel
soundcore              12680  1 snd
lpc_ich                21080  0 
cryptd                 20359  878 ghash_clmulni_intel,aesni_intel,ablk_helper
serio_raw              13462  0 
hid_generic            12548  0 
usbhid                 52659  0 
hid                   106148  2 hid_generic,usbhid
nouveau              1097199  1 
i915                  783961  4 
mxm_wmi                13021  1 nouveau
ttm                    85150  1 nouveau
i2c_algo_bit           13413  2 i915,nouveau
drm_kms_helper         55071  2 i915,nouveau
psmouse               106714  0 
ahci                   25819  2 
drm                   303102  8 ttm,i915,drm_kms_helper,nouveau
e1000e                254433  0 
firewire_ohci          40409  0 
libahci                32716  1 ahci
sdhci_pci              23172  0 
firewire_core          68769  1 firewire_ohci
sdhci                  43015  1 sdhci_pci
ptp                    18933  1 e1000e
crc_itu_t              12707  1 firewire_core
pps_core               19382  1 ptp
video                  19476  2 i915,nouveau
wmi                    19177  3 dell_wmi,mxm_wmi,nouveau
             total       used       free     shared    buffers     cached
Mem:      16310988    4014420   12296568     516340     115636    1288468
-/+ buffers/cache:    2610316   13700672
Swap:     23434236          0   23434236
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.

Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx hibernate hibernate:
/usr/lib/pm-utils/sleep.d/50unload_alx hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Selected interface 'wlan0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:
/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.

Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:
/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.

Wed Nov  5 15:51:04 ART 2014: performing hibernate

```

However, I don't see the resume lines anymore (and I DID see them before)

Looking into /var/log/syslog I notice that the swap partition is being added AFTER the system could NOT load the hibernation image:

```
...
Nov  5 15:55:56 dellores kernel: [    1.466518] device-mapper: uevent: version 1.0.3
Nov  5 15:55:56 dellores kernel: [    1.466571] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
Nov  5 15:55:56 dellores kernel: [    1.466580] ledtrig-cpu: registered to indicate activity on CPUs
Nov  5 15:55:56 dellores kernel: [    1.466663] TCP: cubic registered
Nov  5 15:55:56 dellores kernel: [    1.466729] NET: Registered protocol family 10
Nov  5 15:55:56 dellores kernel: [    1.466869] NET: Registered protocol family 17
Nov  5 15:55:56 dellores kernel: [    1.466879] Key type dns_resolver registered
Nov  5 15:55:56 dellores kernel: [    1.467173] Loading compiled-in X.509 certificates
Nov  5 15:55:56 dellores kernel: [    1.467185] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Nov  5 15:55:56 dellores kernel: [    1.468006] Loaded X.509 cert 'Magrathea: Glacier signing key: e3c165d0891e3ceeb6dd5c18c7e1993cd24956b0'
Nov  5 15:55:56 dellores kernel: [    1.468016] registered taskstats version 1
Nov  5 15:55:56 dellores kernel: [    1.470219] Key type trusted registered
Nov  5 15:55:56 dellores kernel: [    1.471986] Key type encrypted registered
Nov  5 15:55:56 dellores kernel: [    1.473669] AppArmor: AppArmor sha1 policy hashing enabled
Nov  5 15:55:56 dellores kernel: [    1.473673] IMA: No TPM chip found, activating TPM-bypass!
Nov  5 15:55:56 dellores kernel: [    1.474168] regulator-dummy: disabling
Nov  5 15:55:56 dellores kernel: [    1.474280]   Magic number: 6:886:941
Nov  5 15:55:56 dellores kernel: [    1.474396] rtc_cmos 00:05: setting system clock to 2014-11-05 15:55:37 UTC (1415202937)
Nov  5 15:55:56 dellores kernel: [    1.475526] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Nov  5 15:55:56 dellores kernel: [    1.475527] EDD information not available.
Nov  5 15:55:56 dellores kernel: [    1.475550] PM: Hibernation image not present or could not be loaded.
Nov  5 15:55:56 dellores kernel: [    1.476600] Freeing unused kernel memory: 1336K (ffffffff81d20000 - ffffffff81e6e000)
Nov  5 15:55:56 dellores kernel: [    1.476601] Write protecting the kernel read-only data: 12288k
Nov  5 15:55:56 dellores kernel: [    1.478102] Freeing unused kernel memory: 804K (ffff880001737000 - ffff880001800000)
Nov  5 15:55:56 dellores kernel: [    1.479330] Freeing unused kernel memory: 692K (ffff880001b53000 - ffff880001c00000)
Nov  5 15:55:56 dellores kernel: [    1.488105] systemd-udevd[161]: starting version 204
Nov  5 15:55:56 dellores kernel: [    1.498509] wmi: Mapper loaded

....

Nov  5 15:56:02 dellores kernel: [   26.393755] bio: create slab <bio-1> at 1
Nov  5 15:56:02 dellores kernel: [   26.564782] bio: create slab <bio-1> at 1
Nov  5 15:56:02 dellores kernel: [   26.705194] Adding 23434236k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:23434236k FS
Nov  5 15:56:02 dellores kernel: [   26.773997] type=1400 audit(1415213762.802:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=1391 comm="apparmor_parser"
Nov  5 15:56:02 dellores kernel: [   26.774072] type=1400 audit(1415213762.802:12): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=1387 comm="apparmor_parser"
Nov  5 15:56:02 dellores kernel: [   26.774077] type=1400 audit(1415213762.802:13): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1387 comm="apparmor_parser"
Nov  5 15:56:02 dellores kernel: [   26.774080] type=1400 audit(1415213762.802:14): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1387 comm="apparmor_parser"
Nov  5 15:56:02 dellores kernel: [   26.774372] type=1400 audit(1415213762.802:15): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1387 comm="apparmor_parser"
Nov  5 15:56:02 dellores kernel: [   26.774375] type=1400 audit(1415213762.802:16): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1387 comm="apparmor_parser"
Nov  5 15:56:02 dellores kernel: [   26.774526] type=1400 audit(1415213762.802:17): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1387 comm="apparmor_parser"
Nov  5 15:56:02 dellores kernel: [   26.774586] type=1400 audit(1415213762.802:18): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/tcpdump" pid=1394 comm="apparmor_parser"
Nov  5 15:56:02 dellores kernel: [   26.774749] type=1400 audit(1415213762.802:19): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=1386 comm="apparmor_parser"
Nov  5 15:56:02 dellores kernel: [   26.774753] type=1400A audit(1415213762.802:20): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=1386 comm="apparmor_parser"

```

What may have changed? Is there a way to PAUSE the resume process until the swap device is available?

---

