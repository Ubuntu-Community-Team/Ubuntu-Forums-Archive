---
title: "Discussion - https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap"
date: 2012-06-29
forum: Documentation and Community Wiki Discussions
---

### Post by nothingspecial on 2012-06-29
Please use this thread for discussion regarding

[https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap](https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap)

Support threads should be posted in normal forums.

Thank you.

---

### Post by aularon on 2012-08-05
Thanks for the guide, I followed it including regenerating the initramfs, but when rebooting and entering the password on boot, it says
> "cryptsetup: unknown fstype, bad password or options?"when entering the right password.

The following works with no problem after the system boots
```
/sbin/cryptsetup luksOpen /dev/sda7 cryptswap1
```But the code in /usr/share/initramfs-tools/scripts/local-top/cryptroot goes inside the if block at #314
```

                if [ -z "$FSTYPE" ] || [ "$FSTYPE" = "unknown" ]; then
                        message "cryptsetup: unknown fstype, bad password or options?"
                        udev_settle
                        $cryptremove
                        continue
                fi
```
and shows the above message.

Apparently the script isn't recognizing the encrypted filesystem, but I have no idea why.

I am on ubuntu 12.04 (Linux aularon-laptop 3.2.0-27-generic #43-Ubuntu SMP Fri Jul 6 14:25:57 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux).

If there's anything I can try to troubleshoot the problem/solve it? :confused:

---

### Post by zuker on 2012-09-04
Great guide!
But I have a problem: after password query appears system continues to boot and there is no ability to enter the password.

---

### Post by Elfy on 2012-09-04
> **zuker said:**
> Great guide!
But I have a problem: after password query appears system continues to boot and there is no ability to enter the password.

Please start a thread in the normal forums for your issue :)

---

### Post by stylishkoala on 2012-10-24
after applying this steps I need to enter the pass-phrase each time the swap is being mounted or just first time?

---

### Post by JonasHagen on 2012-10-27
Hello,

how can I revert the use of a fixed passphrase to a random one?

I guess I shoud follow the instructions in the wiki and change something at the step
```
sudo cryptsetup luksFormat --cipher aes-cbc-essiv:sha256 --verify-passphrase --key-size 256 /dev/sdXN
```?

---

### Post by sffvba[e0rt on 2012-10-27
> **stylishkoala said:**
> after applying this steps I need to enter the pass-phrase each time the swap is being mounted or just first time?

> **JonasHagen said:**
> Hello,

how can I revert the use of a fixed passphrase to a random one?

I guess I shoud follow the instructions in the wiki and change something at the step
```
sudo cryptsetup luksFormat --cipher aes-cbc-essiv:sha256 --verify-passphrase --key-size 256 /dev/sdXN
```?

This area is for discussing the relevant wiki page(s) and not for support.  For that please post in the relevant subforum.


Regards
404

---

### Post by IQRules on 2012-12-04
Curiously, how much memory you have, and how big the swap space you have here?

Can I have 4GB memory DIM and with 2GB swap space to enable Hibernate?

---

### Post by thelinuxkidd on 2013-05-31
Thanks for the guide. It was very helpful. There was just one extra thing I had to add in order for the passphrase prompt to *always *show up during start-up. In /etc/default/grub I edited GRUB_CMDLINE_LINUX_DEFAULT to look like:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash cryptopts=target=cryptswap1,source=/dev/sda6 resume=swap:/dev/mapper/cryptswap1"

---

### Post by thelinuxkidd on 2013-06-01
> **thelinuxkidd said:**
> Thanks for the guide. It was very helpful. There was just one extra thing I had to add in order for the passphrase prompt to *always *show up during start-up. In /etc/default/grub I edited GRUB_CMDLINE_LINUX_DEFAULT to look like:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash cryptopts=target=cryptswap1,source=/dev/sda6 resume=swap:/dev/mapper/cryptswap1"

I should mention two other things:
1. I only got hibernate to work with tuxonice.
2. By adding the line in the quote to /etc/default/grub (and then rebuilding with upgrade-grub2) I didn't need to edit /usr/share/initramfs-tools/scripts/local-top/cryptroot as mentioned in the guide at the beginning of this thread.


Linux dist: Ubuntu 12.04
Linux kernel: 3.2.0-44-generic-tuxonice
System: Thinkpad T430s

---

### Post by fevrier on 2013-12-30
[FONT=century gothic][SIZE=2]This procedure works nicely with Ubuntu 13.10, with 3 changes:

 - Step 9 (Edit the file /usr/share/initramfs-tools/scripts/local-top/cryptroot) is not needed anymore. The current script will automatically ask for the password of the encrypted swap.

 - Step 10 (Edit the file /etc/acpi/hibernate.sh) is not applicable. This file is not used any more on Ubuntu 13.10.

 - The step 13 needs to be updated to include activating hibernate in logind. See: [https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/1232814](https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/1232814)[/SIZE][/FONT]

---

### Post by el_baby on 2014-11-05
I configured everything as explained on a cleanly installed 14.04 dell precision m4600 and it DID work for some time.

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
Nov  5 15:56:02 dellores kernel: [   26.774753] type=1400 audit(1415213762.802:20): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=1386 comm="apparmor_parser"

```

What may have changed? Is there a way to PAUSE the resume process until the swap device is available?

---

### Post by aleboco on 2014-11-22
Same here... Working well for long time and then repeated failures.

Today I re-ran point 11 and 12 and seems to be working again.

Unreliable...

---

### Post by el_baby on 2014-11-24
> **aleboco said:**
> Same here... Working well for long time and then repeated failures.

Today I re-ran point 11 and 12 and seems to be working again.

Unreliable...

Mmmhhhh this makes me wonder.... maybe the problem arises whenever you install a new kernel. Maybe the initramfs kind of comes preconfigured and it is generated ignoring these settings.

I'll re-run step 12 (I don't need step 11 on Ubuntu 14.04) and check if it stops working when I install a new kernel.

If I can find out what's happening, I'll update the wiki.

---

### Post by jeff_themovie on 2014-11-26
> **el_baby said:**
> Mmmhhhh this makes me wonder.... maybe the problem arises whenever you install a new kernel. Maybe the initramfs kind of comes preconfigured and it is generated ignoring these settings.

I'll re-run step 12 (I don't need step 11 on Ubuntu 14.04) and check if it stops working when I install a new kernel.

If I can find out what's happening, I'll update the wiki.

I have encrypted swap set up and have since upgraded my kernel. update-initramfs should be called as part of the upgrade process, and it should obey your existing settings.

You do need to reboot to the new kernel, because the grub boot menu is configured to boot to newest kernel by default. Suppose you are using kernel A and install a newer kernel B. If you hibernate then boot again, grub will load kernel B, which will conflict with the hibernation image (which was using kernel A). If you manually select kernel A in the grub menu it should resume correctly, but it's best to reboot to the newer kernel anyway.

---

### Post by luis54 on 2015-03-22
Hello,
  I had to reinstall ubuntu 14 in a maching where cryptoswap was working. After the new instalation I have follwed the steps and I am not able to resume from hibernate. The pm-suspend.log finishes as follows:

dom mar 22 19:34:46 CET 2015: performing hibernate

The subsequent syslog indicates that there is a problem with the image

Mar 22 19:35:37 hp kernel: [    0.924768] PM: Hibernation image not present or could not be loaded.

.

---

### Post by DarkDead on 2015-05-01
Has anyone got this working on 14.10 or 15.04?

I just updated a 14.04 machine where I had "hibernate with encrypted swap" running smoothly. With 14.10 and 15.04 the password prompt no longer appears during a normal boot. Strangely it does appear when I boot into recovery mode. The password is accepted and swap mounted as expected. The only difference I noticed is that "swapon -s" reports /dev/dm-0 in filename instead of /dev/mapper/cryptswap1, though I have a vague idea that things were like this on 14.04.

I tried to format my swap partition and redo all steps (skipping 9 and 10 as for 14.04) but to no avail.

This seems akin to [Bug #1359689 cryptsetup password prompt not shown]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1359689"), though the proposed workaround, adding GRUB_GFXPAYLOAD_LINUX=text to /etc/default/grub, has no effect.

---

### Post by DarkDead on 2015-05-02
My issue was indeed due to some misconfiguration in plymouth. I fixed it by replacing plymouth-theme-ubuntu-text for plymouth-theme-lubuntu-logo (any other plymouth-theme-*-logo should work). Now I get the password prompt as expected.

---

### Post by Anders_Bo_Rasmusse on 2015-09-24
I think this should be part of the normal Ubuntu so it works out of the box. Is there any way to make a bounty on it or otherwise try to get it into Ubuntu?

---

### Post by andreas-rabus on 2016-01-10
This Wiki Guide seems to be for upstart not systemd, or all ubuntu versions before 15.04.

systemd seems to try to mount the swap partition before the crypt stuff is setup and fails if the encrpyted swap is tried after crypt setup.
On an arch wiki i found the hint to make the type of the swap partition not "swap", but this did no work for me.

---

### Post by jeff_themovie on 2016-09-28
> **andreas-rabus said:**
> This Wiki Guide seems to be for upstart not systemd, or all ubuntu versions before 15.04.

systemd seems to try to mount the swap partition before the crypt stuff is setup and fails if the encrpyted swap is tried after crypt setup.
On an arch wiki i found the hint to make the type of the swap partition not "swap", but this did no work for me.

Encrypted swap (and hibernate) continues to work for me on Ubuntu 16.04. Granted I set it up a while ago, but that was the procedure I used.

I don't see anything upstart- or systemd-specific with those instructions... Did you set up "regular" encrypted swap (using ecryptfs-setup-swap) before starting? Did you follow the instructions exactly (especially step 8, editing /etc/crypttab)? What do you see when your computer boots?

---

### Post by DarkDead on 2017-01-27
This tutorial does not work for 16.10. I am able to hibernate my computer, but when resuming, it automatically reboots after/when copying the swap contents to RAM (after password input).
Is there any log where I can check what is going wrong? I've been scouring through /var/log/syslog, /var/log/pm-powersave.log and /var/log/pm-suspend.log and found nothing relevant.

At [Hibernation with Ubuntu 16.10 fails - AskUbuntu]("https://askubuntu.com/questions/839147/hibernation-with-ubuntu-16-10-fails") people are pointing out that pm-utils no longer works and we should now use systemd hibernate service. Bullet 5 from [crysman's answer]("https://askubuntu.com/a/849679") implies that hibernation through systemd cannot handle an encrypted swap setup like the tutorial proposes.
Still, I tried adding "pci=nomsi resume=/dev/mapper/cryptswap1" to GRUB_CMDLINE_LINUX_DEFAULT and triggered hibernation with "systemctl hibernate", but the result was the same as above.

Perhaps we should dive into some alternatives:
[How to use hibernation without a swap partition - Debian Wiki]("https://wiki.debian.org/Hibernation/Hibernate_Without_Swap_Partition")
[dm-crypt/Swap encryption with suspend-to-disk support - Arch Wiki]("https://wiki.archlinux.org/index.php/Dm-crypt/Swap_encryption#With_suspend-to-disk_support")

Which one do you think is best?

---

### Post by tworec on 2017-06-08
> **thelinuxkidd said:**
> Thanks for the guide. It was very helpful. There was just one extra thing I had to add in order for the passphrase prompt to *always *show up during start-up. In /etc/default/grub I edited GRUB_CMDLINE_LINUX_DEFAULT to look like:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash cryptopts=target=cryptswap1,source=/dev/sda6 resume=swap:/dev/mapper/cryptswap1"



Similar situation here. Guide is helpful, thx, but it wasn't working until i've read this 
[http://chriseiffel.com/uncategorized/step-by-step-how-to-get-hibernate-working-for-linux-ubuntu-11-04-mint-11/#not-resuming-session](http://chriseiffel.com/uncategorized/step-by-step-how-to-get-hibernate-working-for-linux-ubuntu-11-04-mint-11/#not-resuming-session)
[[here]("http://webcache.googleusercontent.com/search?q=cache:BgTuih1ozp8J:chriseiffel.com/uncategorized/step-by-step-how-to-get-hibernate-working-for-linux-ubuntu-11-04-mint-11/+&cd=9&hl=pl&ct=clnk&gl=pl#not-resuming-session") is google copy of above page]

I've updated [FONT=courier new]/etc/default/grub[/FONT] adding following
```
GRUB_CMDLINE_LINUX=&#8221;resume=/dev/sdXN other-option=value&#8221;
```
than
```
$ sudo update-grub
```
and now its working as a charm.

Can anyone add it to wiki page? It seems I have no permission to do that.

---

### Post by amcsi2 on 2018-06-13
I have my HOME folder encrypted.

I get stuck at this step:

```

swapon --summary

```

All I get is:

```

Filename                Type        Size    Used    Priority
/dev/sda1                                  partition    31249404    0    -2

```

I'm using a swap partition, and the article seems to assume swapfiles. So I don't know how to continue.

---

### Post by el_baby on 2018-06-13
> **amcsi2 said:**
> All I get is:

```

Filename                Type        Size    Used    Priority
/dev/sda1                                  partition    31249404    0    -2
```

I'm using a swap partition, and the article seems to assume swapfiles. So I don't know how to continue.

No. The article assume swap partitions, however, it assumes the swap partition is *already* encrypted (I don't recall 'cause I've done this too long ago, but maybe when you configure encryption during installation it encrypts the swap partition by default).

Anyway, the only thing you should do is encrypt the swap partition which is quite simple to do. Assuming /dev/sda1 is your swap partition (which is what your command shows), just type:
```

sudo ecryptfs-setup-swap
```

This will warn you that hibernate/resume will no longer work (because it will use a random generated encryption key at power-on). Go ahead, since *after* you finish the rest of the instructions, you should be able to hibernate/resume (assuming you remember the passphrase you'll create afterwards).

After you do this,  ```
swapon --summary
``` should give you the expected output.

---

### Post by ogilvierothchild on 2019-12-05
I ran into problems after upgrading to 19.10, but eventually sorted it out.

The instructions here are close to complete, but you also must ensure the **cryptsetup-initramfs** package is installed (ie. run "sudo apt install cryptsetup-initramfs") prior to following the instructions in the ubuntu wiki link above.

For some reason this package was un-installed upon upgrade.

The symptoms I experienced were hangs while booting, errors on the console like  "Gave up waiting for suspend/resume device", and even if you went into grub and added "noresume" on the kernel parameter lines there still might be errors, depending on initramfs configurations and kernel version.

All fixed now, just ensure cryptsetup-initramfs is installed before following the rest of it.

---

### Post by deniz-dezigner on 2020-11-24
It's better to reuse existing **UUID** of swap partition when **mkswap**:
find out **UUID**:
```
sudo blkid
```
copy **UUID** of **/dev/mapper/cryptswap1**, and reuse it (to avoid errors during **update-initramfs**):
```
sudo mkswap -U "YOUR-SWAP-UUID" /dev/mapper/cryptswap1
```

---

### Post by digiworks2 on 2022-08-03
This is really very awesome

---

