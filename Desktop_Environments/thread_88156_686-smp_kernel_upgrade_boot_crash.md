---
title: "686-smp kernel upgrade boot crash"
date: 2005-11-09
forum: Desktop Environments
---

### Post by hounddog32 on 2005-11-09
I have a p4 3.0GHz HT and want to reap the speed benifits of a 686-smp kernel, so I updraded today. However, on re-booting, the boot freezes at the "configuring network interfaces" stage. I'm not talking the 5 minute "searching for DHCP hang", it's a full on crash, ctrl-C won't help unless it's done straight away. I'm only connecting with wireless, if that makes any difference. My wired ethernet is disabled in the bios so is not picked up at all.

I've googled and looked on the forum, seems like an issue noone's had before. Any suggestions?

---

### Post by earobinson on 2005-11-09
what happens if after booting without the network, you enable the network?

---

### Post by hounddog32 on 2005-11-09
It crashes with no interactivity if I later enable the network. I tried ctrl-alt-backspace but it hangs as it is closing down gnome.

---

### Post by hounddog32 on 2005-11-27
I'm pretty sure it's the wireless network - a ralink RT2500. Apparently it doesn't work with a SMP compiled kernel. If you've got boot problems with the same card, try getting rid of SMP!

---

### Post by ekravche on 2005-12-04
I had this problem back when I had Ubuntu 5.04 installed. When I compiled the rt2500 driver and had it enabled in 686-smp the OS just froze.

---

### Post by ekravche on 2005-12-04
After installing the latest and great 686-smp kernel on 5.10 the entire system halts during boot. So it looks like I will be on the 386 kernel for a while until this boot crash os fixed. I'm pretty sure it's because of the rt2500 wireless support in 5.10 that this problem is occuring out of the box for 686-smp.

---

### Post by hounddog32 on 2005-12-04
I'm using the 686 kernel without SMP with no problems. Very frustrating to have either a network connection _or_ a faster CPU, but that's life for now!

---

### Post by crouton on 2005-12-04
You could just disable the network configuration during boot, and have a script that performs the necessary configuration upon login.  That would seem to get around your issue.

---

### Post by hounddog32 on 2005-12-04
What'll happen then is that the system will crash when the network card is enabled - this is a well known issue with the RT2500 driver. There is an alternative driver being worked on that is in the alpha stage, but no other way around at the moment.

---

### Post by teaker1s on 2005-12-04
you installed restricted modules as well? if not that's part of your problem

---

### Post by ekravche on 2005-12-04
[QUOTE=crouton]You could just disable the network configuration during boot, and have a script that performs the necessary configuration upon login.  That would seem to get around your issue.[/QUOTE]

Not sure about 5.10 but in 5.04 your approach still halted the OS. After compiling, installing, and initializing the driver in a session without logging out and restarting the OS still halted for me. I've realized now that this problem is partially to do with the fact that my processor is a intel P4 515 2.93Mhz, which doesn't support HT or anything fancy like that. So it was a user error on my part. I'm runnning the 686 kernel just fine now.

---

### Post by Cuppa-Chino on 2005-12-10
hi,

got an odd similar behavoiur... have 
p4 2.4ghz
kernel  2.6.12-10-686-smp
acx 111 wireless card running via ndiswrapper

and the system freezes completely on first boot of the day, need to push reset button, but after that comes up smoothly... any ideas what to do?

last bit of syslog during freeze:
```

Dec 10 17:58:42 localhost kernel: [4294749.928000] Bluetooth: RFCOMM TTY layer initialized
Dec 10 17:58:42 localhost anacron[9859]: Anacron 2.3 started on 2005-12-10
Dec 10 17:58:42 localhost anacron[9859]: Normal exit (0 jobs run)
Dec 10 17:58:42 localhost /usr/sbin/cron[9884]: (CRON) INFO (pidfile fd = 3)
Dec 10 17:58:42 localhost /usr/sbin/cron[9885]: (CRON) STARTUP (fork ok)
Dec 10 17:58:42 localhost /usr/sbin/cron[9885]: (CRON) INFO (Running @reboot jobs)
Dec 10 17:59:01 localhost kernel: [4294768.956000] ndiswrapper (iw_set_encr:892): removing encryption key 0 failed (C0010015)
Dec 10 17:59:01 localhost kernel: [4294768.956000] ndiswrapper (iw_set_encr:892): removing encryption key 1 failed (C0010015)
Dec 10 17:59:01 localhost kernel: [4294768.956000] ndiswrapper (iw_set_encr:892): removing encryption key 2 failed (C0010015)
Dec 10 17:59:01 localhost kernel: [4294768.956000] ndiswrapper (iw_set_encr:892): removing encryption key 3 failed (C0010015)
Dec 10 17:59:01 localhost kernel: [4294768.957000] ndiswrapper (iw_set_encr:892): removing encryption key 0 failed (C0010015)
Dec 10 18:02:28 localhost syslogd 1.4.1#17ubuntu3: restart.

```

sucessful boot:
```

Dec 10 18:02:34 localhost kernel: [4294752.816000] Bluetooth: RFCOMM TTY layer initialized
Dec 10 18:02:34 localhost anacron[9850]: Anacron 2.3 started on 2005-12-10
Dec 10 18:02:34 localhost anacron[9850]: Normal exit (0 jobs run)
Dec 10 18:02:34 localhost /usr/sbin/cron[9875]: (CRON) INFO (pidfile fd = 3)
Dec 10 18:02:34 localhost /usr/sbin/cron[9876]: (CRON) STARTUP (fork ok)
Dec 10 18:02:34 localhost /usr/sbin/cron[9876]: (CRON) INFO (Running @reboot jobs)
Dec 10 18:02:38 localhost kernel: [4294757.325000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Dec 10 18:02:38 localhost kernel: [4294757.325000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Dec 10 18:02:43 localhost gconfd (johnny-10003): starting (version 2.12.0), pid 10003 user 'johnny'

```

---

### Post by Cuppa-Chino on 2005-12-11
booted straight through for the first time in forever today... probably because its Sunday or someting like that

help would still be appreciated ;)

---

### Post by Cuppa-Chino on 2005-12-14
***bump***

also more on that front, had a frightful day booting today:

have installed kernel 686-_no smp_ on the machine and thought I would see what today brings

[LIST=1]
[*]686smp would not boot - ALSA error?
[*]686smp would not boot again, frooze will entering into Gnome with sound looping
[*]686 NO-smp would not boot - no ALSA error
[*]686 NO-smp booted then tried to get NDISWRAPPER working on that, booted right back but it just does not have a wireless device
[*]booted windows to do some emails!
[*]booted 686smp okay
[/LIST]

what is going on where shall I look? what to do? [SIZE="3"]help[/SIZE] [SIZE="2"]help[/SIZE] [SIZE="1"]help:( [/SIZE]

[SIZE="1"]*PS : downloading gentoo at the moment*[/SIZE]

---

### Post by hounddog32 on 2005-12-14
Cuppa-Chino, what processor is it again? If it's a P4 without Hyper threading, you're wasting your time installing SMP - SMP is for multi-processor systems (HT is kind-of multi-processor) 

686 without SMP will work fine with the RT2500. I've not used ndiswrapper, but i assume that it should be equally good.

Your wireless card is different, i have no idea from that what's gone wrong there.

---

### Post by Cuppa-Chino on 2005-12-14
[QUOTE=hounddog32]Cuppa-Chino, what processor is it again? If it's a P4 without Hyper threading, you're wasting your time installing SMP - SMP is for multi-processor systems (HT is kind-of multi-processor) [/QUOTE]

Specs:
P4 2.4GHz C  **HT** - 800MHz FSB - Asus P4P800 - PC4000 RAM <== all not overclocked at the moment and running really stable in Windof$, Memtest etc etc

Radeon 9700Pro & Creative Audigy 2ZS for multimedia

Trendnet PCI423 Wireless card based on ACX111 chipset, runs fine once going with Ndiswrapper - if system comes up this does not cause any problems really
:arrow: will try and remove auto wlan0 ?? and see if that helps boot stability
[QUOTE=hounddog32]
686 without SMP will work fine with the RT2500. I've not used ndiswrapper, but i assume that it should be equally good.

Your wireless card is different, i have no idea from that what's gone wrong there.[/QUOTE]

cannot get ndiswrapper to work in non-smp kernel , any ideas

---

### Post by Cuppa-Chino on 2005-12-17
had another crash and have trawled the records to find **_anything_**

syslog:
```
Dec 17 19:52:17 localhost kernel: [4297184.070000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Dec 17 19:57:21 localhost kernel: [4297487.584000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Dec 17 19:57:21 localhost kernel: [4297487.584000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Dec 17 20:00:57 localhost kernel: [4297703.878000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Dec 17 20:00:57 localhost kernel: [4297703.878000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Dec 17 20:02:05 localhost kernel: [4297771.598000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Dec 17 20:02:05 localhost kernel: [4297771.598000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Dec 17 20:15:45 localhost kernel: [4298591.999000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Dec 17 20:15:45 localhost kernel: [4298591.999000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Dec 17 20:16:55 localhost kernel: [4298662.076000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Dec 17 20:16:55 localhost kernel: [4298662.076000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Dec 17 20:17:01 localhost /USR/SBIN/CRON[12276]: (root) CMD (   run-parts --report /etc/cron.hourly)
Dec 17 20:17:57 localhost kernel: [4298723.956000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Dec 17 20:17:57 localhost kernel: [4298723.956000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Dec 17 20:19:28 localhost kernel: [4298814.856000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Dec 17 20:19:28 localhost kernel: [4298814.856000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Dec 17 20:22:22 localhost kernel: [4298988.788000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Dec 17 20:22:22 localhost kernel: [4298988.788000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Dec 17 20:22:52 localhost kernel: [4299019.297000] ndiswrapper (iw_set_encr:892): removing encryption key 0 failed (C0010015)
Dec 17 20:22:52 localhost kernel: [4299019.297000] ndiswrapper (iw_set_encr:892): removing encryption key 1 failed (C0010015)
Dec 17 20:22:52 localhost kernel: [4299019.297000] ndiswrapper (iw_set_encr:892): removing encryption key 2 failed (C0010015)
Dec 17 20:22:52 localhost kernel: [4299019.297000] ndiswrapper (iw_set_encr:892): removing encryption key 3 failed (C0010015)
Dec 17 20:22:52 localhost kernel: [4299019.297000] ndiswrapper (iw_set_encr:892): removing encryption key 0 failed (C0010015)
Dec 17 20:24:24 localhost kernel: [4299111.259000] ndiswrapper (iw_set_encr:892): removing encryption key 0 failed (C0010015)
Dec 17 20:24:24 localhost kernel: [4299111.259000] ndiswrapper (iw_set_encr:892): removing encryption key 1 failed (C0010015)
Dec 17 20:24:24 localhost kernel: [4299111.260000] ndiswrapper (iw_set_encr:892): removing encryption key 2 failed (C0010015)
Dec 17 20:24:24 localhost kernel: [4299111.260000] ndiswrapper (iw_set_encr:892): removing encryption key 3 failed (C0010015)
Dec 17 20:24:24 localhost kernel: [4299111.260000] ndiswrapper (iw_set_encr:892): removing encryption key 0 failed (C0010015)
Dec 17 20:24:41 localhost kernel: [4299127.740000] ndiswrapper (iw_set_encr:892): removing encryption key 0 failed (C0010015)
Dec 17 20:24:41 localhost kernel: [4299127.740000] ndiswrapper (iw_set_encr:892): removing encryption key 1 failed (C0010015)
Dec 17 20:24:41 localhost kernel: [4299127.740000] ndiswrapper (iw_set_encr:892): removing encryption key 2 failed (C0010015)
Dec 17 20:24:41 localhost kernel: [4299127.740000] ndiswrapper (iw_set_encr:892): removing encryption key 3 failed (C0010015)
Dec 17 20:24:41 localhost kernel: [4299127.741000] ndiswrapper (iw_set_encr:892): removing encryption key 0 failed (C0010015)
Dec 17 20:25:23 localhost kernel: [4299170.494000] ndiswrapper (iw_set_encr:892): removing encryption key 0 failed (C0010015)
Dec 17 20:25:23 localhost kernel: [4299170.494000] ndiswrapper (iw_set_encr:892): removing encryption key 1 failed (C0010015)
Dec 17 20:25:23 localhost kernel: [4299170.494000] ndiswrapper (iw_set_encr:892): removing encryption key 2 failed (C0010015)
Dec 17 20:25:23 localhost kernel: [4299170.494000] ndiswrapper (iw_set_encr:892): removing encryption key 3 failed (C0010015)
Dec 17 20:25:23 localhost kernel: [4299170.494000] ndiswrapper (iw_set_encr:892): removing encryption key 0 failed (C0010015)
Dec 17 20:25:45 localhost kernel: [4299192.078000] ndiswrapper (iw_set_encr:892): removing encryption key 0 failed (C0010015)
Dec 17 20:25:45 localhost kernel: [4299192.078000] ndiswrapper (iw_set_encr:892): removing encryption key 1 failed (C0010015)
Dec 17 20:25:45 localhost kernel: [4299192.079000] ndiswrapper (iw_set_encr:892): removing encryption key 2 failed (C0010015)
Dec 17 20:25:45 localhost kernel: [4299192.079000] ndiswrapper (iw_set_encr:892): removing encryption key 3 failed (C0010015)
Dec 17 20:25:45 localhost kernel: [4299192.079000] ndiswrapper (iw_set_encr:892): removing encryption key 0 failed (C0010015)
Dec 17 20:27:16 localhost syslogd 1.4.1#17ubuntu3: restart.
```

so could this be an NDISWRAPPER ISSUE? I have NDISWRAPPER 1.6 installed and am using WPA Encryption - please help me...

---

### Post by hounddog32 on 2005-12-18
'fraid I cant help - I've got no experience with ndiswrapper. I'm sure you'll find something on here if you search or make a new thread.

---

### Post by antidrugue on 2005-12-18
[quote=teaker1s]you installed restricted modules as well? if not that's part of your problem[/quote]

Right.

What gives you:

```

dpkg --get-selections | grep 686

```

and 

```

dpkg --get-selections | grep 386

```

?

I guest you add the restricted modules installed with the 386 kernel, and that you just install the 686-smp kernel without attention to the needed modules...

Anyway if you want real performance, compile your own kernel and modules;)

It's a lot simpler then it sounds... :p

---

