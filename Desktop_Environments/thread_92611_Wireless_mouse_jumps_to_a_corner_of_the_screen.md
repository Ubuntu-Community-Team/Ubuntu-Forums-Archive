---
title: "Wireless mouse jumps to a corner of the screen"
date: 2005-11-20
forum: Desktop Environments
---

### Post by iH8forcedRegistration on 2005-11-20
I have a Logitech MediaPlay wireless USB mouse. When this mouse is plugged in using the PS2 adapter, only about half the buttons work, but the pointer tracking is superb. When the mouse is plugged in using USB, all the buttons work (thanks to [evrouter]("http://www.bedroomlan.org/~alexios/coding_evrouter.html")), but every now and then, the pointer jumps to the corner of the screen and gets stuck there for about a second. When I'm working, it's just a minor annoyance, but when I'm playing [games]("http://legendsthegame.net"), a jump at a critical moment means instant death.

I have not been able to correlate this jump to anything else going on in my system. I've tried unplugging other usb devices, but that did nothing. I've tried having a second mouse connected to the PS2 port. That also did nothing. I spent about two hours checking dmesg periodically, and found no unusual entries around the time the pointer jump happened.

Here's the relevant section of my xorg.conf
```

Section "InputDevice"
    Identifier  "USB Mouse"
    Driver       "mouse"
    Option      "CorePointer"
    Option      "Device"                "/dev/input/event*"
    Option      "Protocol"              "evdev"
    Option      "ZAxisMapping"          "4 5 7 6"
    Option      "Buttons" "12"
    Option      "Dev Name" "Logitech USB Receiver"
    Option      "Resolution" "800"
EndSection

```

There is [a driver written specifically for the Logitech MediaPlay mouse]("http://daemon.prozone.ws/~david/projects/lmpcm_usb/"), but I can't use it because it conflicts with usbhid, which my keyboard uses.

I've been guessing at how to solve this for a while, and it recently occurred to me that perhaps the issue was related to the fact that PS2 mice were supported directly by the kernel, but that USB mice were in a module. So, I recompiled my kernel with usb and usbhid built in instead of as modules. That actually improved the situation slightly-- the pointer still jumps, but it doesn't happen as often, and when it does, it recovers faster.

If anyone has any idea how I can make this problem go away for good, please let me know.

---

### Post by kruz on 2005-11-20
sounds like an ev problem
eg evdev and evrouter i do believe

---

### Post by iH8forcedRegistration on 2005-11-20
[QUOTE=kruz]sounds like an ev problem
eg evdev and evrouter i do believe[/QUOTE]
Apart from compiling evdev into my kernel (which I'm doing now, and which I should have thought of earlier), is there anything else I should do to try to troubleshoot evdev?

---

### Post by iH8forcedRegistration on 2005-11-20
I now have evdev, mousedev, and tsdev compiled into my kernel. Again, the problem has gotten less frequent, but it still happens. 

Since this keeps working better and better, I'm thinking there's probably just some other usb-related thing I'm missing. Kernels and such are well over my head, so I'll put a copy of my lsmod here. If you see anything that might help if it were compiled directly into the kernel, please let me know
```

Module                  Size  Used by
ipx                    25388  0 
nls_iso8859_1           4224  1 
nls_cp437               5888  1 
vfat                   12288  1 
fat                    46620  1 vfat
nvidia               3712008  24 
rfcomm                 34972  0 
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
speedstep_lib           4228  0 
cpufreq_powersave       1920  0 
cpufreq_stats           5124  0 
cpufreq_userspace       4444  0 
cpufreq_ondemand        5916  0 
cpufreq_conservative     6820  0 
freq_table              4484  1 cpufreq_stats
ipt_limit               2432  8 
iptable_mangle          2816  0 
ipt_LOG                 6272  8 
ipt_MASQUERADE          3328  0 
iptable_nat            20948  1 ipt_MASQUERADE
ipt_TOS                 2432  0 
ipt_REJECT              5248  1 
ip_conntrack_irc       71824  0 
ip_conntrack_ftp       72336  0 
ipt_state               2048  6 
ip_conntrack           39864  5 ipt_MASQUERADE,iptable_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
iptable_filter          2944  1 
ip_tables              18176  9 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,iptable_nat,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
tc1100_wmi              6916  0 
video                  16004  0 
battery                 9604  0 
container               4608  0 
i2c_acpi_ec             5760  0 
button                  6672  0 
pcc_acpi               11392  0 
sony_acpi               5516  0 
ac                      4996  0 
dev_acpi               11396  0 
hotkey                  9508  0 
ipv6                  217024  10 
sd_mod                 17552  2 
snd_mpu401              6344  0 
snd_mpu401_uart         6784  1 snd_mpu401
snd_rawmidi            22816  1 snd_mpu401_uart
snd_seq_device          8204  1 snd_rawmidi
analog                 10528  0 
gameport               14472  1 analog
floppy                 52692  0 
pcspkr                  3652  0 
rtc                    11704  0 
sis900                 19456  0 
mii                     5248  1 sis900
ehci_hcd               29576  0 
ohci_hcd               18564  0 
ohci1394               30516  0 
i2c_sis96x              5252  0 
i2c_core               19728  2 i2c_acpi_ec,i2c_sis96x
pci_hotplug            25012  0 
sis_agp                 8452  1 
agpgart                32328  2 nvidia,sis_agp
dm_mod                 52028  1 
joydev                  9408  0 
sr_mod                 15652  0 
sbp2                   21000  0 
ieee1394               91192  2 ohci1394,sbp2
psmouse                26116  0 
parport_pc             31940  1 
lp                     11460  0 
parport                32072  2 parport_pc,lp
ide_cd                 37124  0 
cdrom                  33952  2 sr_mod,ide_cd
md                     40912  0 
ext3                  115976  1 
jbd                    48408  1 ext3
ide_disk               16128  6 
ide_generic             1664  0 
sis5513                14344  1 
unix                   24624  557 
thermal                13192  0 
processor              23100  1 thermal
fan                     4740  0 
capability              5000  0 
commoncap               6912  1 capability          

```

---

### Post by rhino_harley on 2006-12-10
I am having this problem as well. I am using a Evoluent ergonomic mouse. Occasionally the mouse will get in one the of corners. For example it will get stuck hovering over the recycle bin. I have discovered that if I lift the mouse off the mouse pad it will not be stuck anymore.

Did you ever find a solution to this problem?

---

### Post by iH8forcedRegistration on 2006-12-10
**My Saga**
Not really. After I found out that the problem also occurs when the mouse is connected to my Powerbook, I decided to call Logitech and give them a hard time. They said that it was actually a hardware problem with the mouse, and that I should download some installer from their website, which, conveniently, is only available for windows.

I considered taking the mouse with me to a public lab and installing the drivers on a Windows machine, but after several months of trying to trick Logitech's technical support to actually *read* my e-mails before responding with a "stupid user" form letter, I managed to get them to tell me that it's actually a driver workaround rather than a firmware patch. 

It only took me twenty minutes to determine that I had no hope of ever managing to add the same workaround to xorg. It's sources are considerably more complicated than anything I've ever managed to patch. I rather doubt that I could have even *found* the code I needed to change among the megabytes of source.

**Not-at-all helpful response to your question**
If we assume for a moment that your mouse doesn't have the same stupid hardware problem, all I can really give you are the standard "underestimating your intelligence" technical support replies.

[LIST]
[*]Make sure there isn't any crap on the lens
[*]Try a different mouse pad
[*]Replace the batteries (if it's wireless)
[*]Move the receiver closer to the mouse itself (wireless)
[/LIST]

The good news is that this thread should get bumped to the top of the forum, so you might get some better responses from people smarter than me :)

---

### Post by Hendrixski on 2006-12-11
I know that this is going to sound weird, but I had the same problem when I first plugged in my brand new mouse this morning.  I was watching the news at the time so I was using a magazine as my mouse pad and was really concerned because my mouse would rocket up to the top left corner of the screen every so often... So then I switched to using a hardcover book as my mousepad and problem solved.  So... are you sure that you are using a flat surface as your mousepad?

---

### Post by Dave54 on 2006-12-11
I've had some awful experiences with surfaces under optical mice.

I have found that the surface the mouse is used on should be flat with a dense non-repeating texture to it, and absolutely no shine or finish.

I have come across some mouse pads that have made my mouse unusable, while others work fine. If all else fails, keep trying new surfaces.

---

### Post by rhino_harley on 2006-12-11
Nope, I am using a mouse pas on top of a desk. Can't believe I am the only one who has encountered from this issue.

---

### Post by Chonnawonga on 2006-12-13
Yep, I'm having this problem too. For the record, it's a Logitech USB optical corded mouse. I have no idea what's going on with that.

---

