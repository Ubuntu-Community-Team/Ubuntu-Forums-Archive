---
title: "System crashes - caps LED flashing"
date: 2008-12-05
forum: General Help
---

### Post by greew on 2008-12-05
Hi all,

I've search through other threads dealing with kernel panic and flashing LEDs, but none seems to be related to my problem:

Twice today I've left my computer for a few minutes, just to return to a crashed machine. All graphics is left on the screen, but keyboard and mouse doesn't respond.

The first time I just accepted it, but this second time I try to found out whats wrong.

As a first I went for the syslog - and got a really big scare. The syslog started this morning at 7.30 (say a little more than 12 hours) has a size of 808MB (say 9 mio. lines) :o After looking through the first about 3900 lines, which seems all right, suddenly I get this message: 
```

Dec  5 19:10:14 jesper-laptop kernel: [29904.397350] BUG: scheduling while atomic: swapper/0/0x00000100
Dec  5 19:10:14 jesper-laptop kernel: [29904.397364] Modules linked in: tun ipv6 isofs udf crc_itu_t af_packet binfmt_misc rfcomm bridge stp bnep sco l2cap ppdev vmnet vmblock v
mci vmmon acpi_cpufreq cpufreq_ondemand cpufreq_powersave cpufreq_conservative cpufreq_stats freq_table cpufreq_userspace wmi sbs container sbshc pci_slot iptable_filter ip_tabl
es x_tables uinput sbp2 parport_pc lp parport pcspkr arc4 serio_raw psmouse ecb crypto_blkcipher joydev evdev btusb bluetooth iwlagn iwlcore snd_hda_intel rfkill snd_pcm_oss sdh
ci_pci snd_mixer_oss sdhci mac80211 mmc_core ricoh_mmc snd_pcm iTCO_wdt uvcvideo compat_ioctl32 videodev cfg80211 iTCO_vendor_support v4l1_compat nvidia(P) snd_seq_dummy i2c_cor
e video snd_seq_oss output snd_seq_midi snd_rawmidi snd_seq_midi_event tpm_infineon tpm snd_seq tpm_bios battery asus_laptop ac snd_timer snd_seq_device snd led_class intel_agp 
agpgart button soundcore snd_page_alloc shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom sd_mod crc_t10dif ata_piix sg ata_generic usbhid hid pata_a
Dec  5 19:10:14 jesper-laptop kernel: pi ahci ohci1394 libata ieee1394 scsi_mod uhci_hcd dock ehci_hcd usbcore e1000e thermatenbF0cdna69ee4h1[207</9]]20 dcviotepr3 b00/[
Dec  5 19:10:14 jesper-laptop kernel: 59e7_hcea00</90]2 adcviaoreii ahci ohci1394 libata ieee1394 scr3 5E8 0. c84][t]014.tic2[=s0f_fa bm_ st<40C0]= 8[7t_39/ 4 tc 
Dec  5 19:10:14 jesper-laptop kernel: eieco_tbnii_ior544100c<0?5t_39/ 9 t6c29=s0f_oa wmd  01a00040p1e5ob t]019.t6]ae>e9tt6cc20=0f _a wmd ud- . Db/]p>14.t6c2[=01f_eawdlmuc,0C :4c
 b05ob[t]] ..0cc20=0f _abwmd  00e4904=]b051b t]]144tic2[=0fc_sawmd u0t bitblit softcursor fuse
Dec  5 19:10:14 jesper-laptop kernel: [29904,: 0d.11ei254]e9.t6t_=0_abwdms ub,Lx0 6R14t10a54b t]0e9.4t6cc2r=s0f _sa wmlmu d.  01Db1  0e512y51]0e9.4t6cc2r=s0fc_ea wsl_  d(0 :9Db1
ob0 e[?>4 t6ce2[==0fc_fabwd _ ud,0 :9Db1  0e512y51]0e9.4t6cc2r=01f _saw m lust0 b4204[41i4o][t]0e9.4t6cc2r=01f _sawbmdpuct0i.7:.]=pp0a5t_39ie940tc]
Dec  5 19:10:15 jesper-laptop kernel: /ietcp_sbndnpxilric #1)500a5ee302/e9.4t6cc2r=s0f_ea wsl_  d(0 :9Db1   s512ya
Dec  5 19:10:15 jesper-laptop vmnetBridge: RTM_NEWLINK: name:wlan0 index:4 flags:0x00011043 
Dec  5 19:10:15 jesper-laptop vmnetBridge: Can't add interface wlan0 4 (does exist). 
Dec  5 19:10:15 jesper-laptop kernel: e904t6cc2r=s0fc_ea wsl_  dt bitblit softcursor fuse

```

This keeps going on forever and ever (the next probably 800 MB). The end of all this is:
```

Dec  5 19:50:12 jesper-laptop kernel: [32301[9+.4.2x6<4>[32301.665272]  [<f887da43>] ? ticks_elapsed_in_us+0xb/0x4d [pro5i+.4.2x6<4>[32301.668219]  [<f8i+.4.2c/<4>[32301.670037]  [<f887da43>] ? ticks_elapsed_in_us+0xb/0x4d [processor]
Dec  5 19:51:54 jesper-laptop syslogd 1.5.0#2ubuntu6: restart.
Dec  5 19:51:54 jesper-laptop kernel: Inspecting /boot/System.map-2.6.27-9-generic

```

Apparently this had been going on for 40 minutes :o

Does anyone have an idea to why this is happening? If you'd like something from the syslog file, I'll happily add it.

I'm kinda lost to what's happening here???

Best regards - and thanks in advance :)

- Jesper

---

### Post by ajmorris on 2008-12-06
hi there,
can i please have the output of:
```
sudo uname -a
```

and also, could you please pastebin your whole /var/log/syslog. (or you could paste it here in [code] envelops.

And also, could you do the same with your /var/log/messages.

I would preferably like the files, directly after a reboot from one of your crashes, if possible.


AJ

---

### Post by greew on 2008-12-06
> **ajmorris said:**
> hi there,
can i please have the output of:
```
sudo uname -a
```

and also, could you please pastebin your whole /var/log/syslog. (or you could paste it here in ```
 envelops.

And also, could you do the same with your /var/log/messages.

I would preferably like the files, directly after a reboot from one of your crashes, if possible.


AJ

Hi AJ,

First:
[CODE]
jesper@jesper-laptop:~$ sudo uname -a
Linux jesper-laptop 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux

```

I don't know how large files pastebin accepts, but I doubt that they will accept my 808MB syslog file, and my 758MB messages file??

Should I instead take the first 1000 lines around where it looks like, where the problem begins, and the last 1000 lines up to where the crash happens of the syslog and messages files??

Best regards,
- Jesper

---

### Post by greew on 2008-12-06
I've made 4 logs now

The messages log file where the dump data begins (Dec  5 19:10:14)
[http://pastebin.com/m6eb42178](http://pastebin.com/m6eb42178)

The messages log file where the dump data ends 
[http://pastebin.com/m784ef825](http://pastebin.com/m784ef825)

The syslog file where the dump data begins (Dec  5 19:10:14)
[http://pastebin.com/m6ce19ba9](http://pastebin.com/m6ce19ba9)

The syslog log file where the dump data ends 
[http://pastebin.com/m6ec64a2d](http://pastebin.com/m6ec64a2d)

---

### Post by greew on 2008-12-06
I can see that the first line from syslog tells this:
```

Dec  5 19:10:14 jesper-laptop kernel: [29904.397350] BUG: scheduling while atomic: swapper/0/0x00000100

```

If it is of any help? 

:)

---

### Post by ajmorris on 2008-12-07
woah, they are HUGE!  do:
```
sudo rm /var/log/syslog && sudo rm /var/log/messages
```

Then reboot, and paste the contents of the files, after your next crash :)

(BTW, just so you know, this seems to be quite a regular occurrence with the ubuntu 2.6.27.* kernels. I have been trying a few different people's log files to try to determine the root of the problem)

AJ

---

### Post by greew on 2008-12-07
> **ajmorris said:**
> woah, they are HUGE!  do:
```
sudo rm /var/log/syslog && sudo rm /var/log/messages
```

Then reboot, and paste the contents of the files, after your next crash :)

(BTW, just so you know, this seems to be quite a regular occurrence with the ubuntu 2.6.27.* kernels. I have been trying a few different people's log files to try to determine the root of the problem)

AJ

Ok, I'll do that. 

Thanks so far, AJ :KS

---

### Post by greew on 2008-12-08
Hi again AJ (and others watching/helping/having the same problem) :)

Crashed happened again today.
I wasn't at my computer when it happened, but nearby. Suddenly I could hear my net radio crashing, went to my computer, and it was dead again.

Here are the logs right after the crash
syslog: [http://pastebin.com/m7c7d154f](http://pastebin.com/m7c7d154f)
messages: [http://pastebin.com/m20156489](http://pastebin.com/m20156489)
kern.log: [http://pastebin.com/mf1eb03e](http://pastebin.com/mf1eb03e)

I hope this is of some help to you :)

---

### Post by ajmorris on 2008-12-09
What wireless card do you have?
(post the output of sudo lspci | grep -i network)


AJ

---

### Post by iponeverything on 2008-12-09
I see your driver is iwlagn.

Please see: [https://bugs.launchpad.net/linux/+bug/276990](https://bugs.launchpad.net/linux/+bug/276990)

To verify that it is the cause of the problem, do have a another wireless device that you can use -- to see if the crash still happens.  If you do, do --

```
sudo ifconfig wlan0 down
sudo rmmod iwlagn
```

before you pop in the other card.

What release are you using - 8.10?

---

### Post by greew on 2008-12-09
ajmorris:
lspci | grep -i network gives me:
```

00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
05:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

```

iponeverything:
I've had a look at the bug and i'll try to install the latest wireless driver to see if this makes the bug disappear.

And yes, using 8.10 :)

---

### Post by mbeierl on 2008-12-09
Ok, I have an Intel wireless too:

0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

and have been having random crashes too (flashing leds), and I just narrowed it down to when I'm on wireless, not wired.  I couldn't figure out at first why my laptop suddenly became so unstable whenever I was traveling, but only in the airport, not in the air.

---

### Post by ajmorris on 2008-12-09
> **mbeierl said:**
> Ok, I have an Intel wireless too:

0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

and have been having random crashes too (flashing leds), and I just narrowed it down to when I'm on wireless, not wired.  I couldn't figure out at first why my laptop suddenly became so unstable whenever I was traveling, but only in the airport, not in the air.


check out the above bug report link posted... you are probably using the same drivers... to make sure, run:
```
lsmod | grep -i iwlagn
```


AJ

---

### Post by iponeverything on 2008-12-10
On the Launchpad bug see:

bh1nd3r 2008-12-06:

It looks like you might be in luck. Apparently the crashes stop in the -10 kernel.

---

### Post by Casper Hansen on 2008-12-12
> **iponeverything said:**
> On the Launchpad bug see:

bh1nd3r 2008-12-06:

It looks like you might be in luck. Apparently the crashes stop in the -10 kernel.

I had three crashes today, but haven't had it in a long time with the -10 kernel.

---

### Post by greew on 2008-12-12
Currently i've disabled the ability to use 802.11n in my router. This has "solved" the problem so far.

When I get the -10 kernel, I'll try to enable it again and see if I still get crashes!

Thanks so far everyone! :D

- Jesper

---

