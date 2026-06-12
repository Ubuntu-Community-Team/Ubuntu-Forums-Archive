---
title: "Variable boot times"
date: 2011-08-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by John_Rose1 on 2011-08-02
I have a Dell Vostro 3700 running on dual boot Ubuntu 10.04 Lucid Lynx and Windows XP Professional under Grub2.


The Grub2 menu invariably comes up normally and Windows invariably boots normally.


However, for Ubuntu there are two categories of boots:



1. Less than half of the time: &#8220;normal&#8221; boot in which the GNOME login comes less than 20 seconds seconds after Grub2 menu selection (during the boot there is I/O on the hard drive and blinking cursor at upper left of the screen).
 2. More than half of the time: delayed boot in which there is an additional annoying delay of about 45 seconds before the GNOME login &#8211; screen is blank with no cursor, WiFi and blue-tooth LEDs on but very little if any hard drive I/O).
 

 There have been different hardware versions of the Dell Vostro 3700 which are not distinguished by name or model number. My machine (the standard version delivered in most markets since mid-2010) has an integrated Intel Media Accelerator HD video card and a nVidia Geforce 330M card; these are connected with the nVidia "Optimus" hardware technology which is supposed to use the Intel card on battery and the nVidia card on main power. The web is full of frustrations of Linux users who cannot access the nVidia card on their computers, apparently because neither Dell nor nVidia has provided the software support for access to both cards under Linux. Thus my Ubuntu is using only the Intel HD video card.
 

 The Dell Vostro 3700 was certified by Ubuntu ([COLOR=#000080]_[http://www.ubuntu.com/certification/hardware/201001-4961:201004-5579](http://www.ubuntu.com/certification/hardware/201001-4961:201004-5579)_[/COLOR]) but specifically mentioning Ubuntu 10.10 (I have 10.04) and the Intel HD card. Unfortunately it is not clear whether the Vostro tested was the original version with discrete access to the nVidia card or the more recent one (like mine) with switched access.
 

 I am attaching boot charts for sample normal and delayed boots. These show that gdm-binary loads after more than 40 seconds in the delayed boot and after less than 20 seconds in the "normal" boot.


During both types of boot there are ALSA polling errors in the system messages, but in the delayed boot there is a 47 second break between the first and second polling error (see below), while in the normal boot there is at most a 2 second gap between polling errors.



```

 
Boot + 1 sec: ALSA hda_intel.c:1420: Codec #1 probe error; disabling it...

Boot + 48 secs:
Jul 30 08:28:25 JOHN-PC kernel: [   22.090458] ALSA hda_intel.c:1420: Codec #2 probe error; disabling it...
Jul 30 08:28:25 JOHN-PC kernel: [   23.502836] ALSA hda_intel.c:1420: Codec #3 probe error; disabling it...
Jul 30 08:28:25 JOHN-PC kernel: [   24.915198] ALSA hda_intel.c:1420: Codec #4 probe error; disabling it...
Jul 30 08:28:25 JOHN-PC kernel: [   26.327581] ALSA hda_intel.c:1420: Codec #5 probe error; disabling it...
Jul 30 08:28:25 JOHN-PC kernel: [   27.739944] ALSA hda_intel.c:1420: Codec #6 probe error; disabling it...
Jul 30 08:28:25 JOHN-PC kernel: [   29.152314] ALSA hda_intel.c:1420: Codec #7 probe error; disabling it...
Jul 30 08:28:25 JOHN-PC kernel: [   30.564818] __ratelimit: 9 callbacks suppressed
Jul 30 08:28:25 JOHN-PC kernel: [   30.565281] HDA Intel 0000:01:00.1: PCI INT A disabled
Jul 30 08:28:25 JOHN-PC kernel: [   60.499253] ALSA hda_intel.c:712: azx_get_response timeout, switching to polling mode: last cmd=0x00af0700
Jul 30 08:28:25 JOHN-PC kernel: [   68.855199] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
Jul 30 08:28:25 JOHN-PC kernel: [   68.855201] vgaarb: transferring owner from PCI:0000:00:02.0 to PCI:0000:01:00.0

``` 


I have seen several slow boot complaints with Lucid, but none with variable slow and normal booting.

 

I am not sure whether the above Intel HD recognition problem is related to the Optimus technology (and thus perhaps not be readily solvable), or could perhaps be fixed by standard configuration for the Intel HD card, or is perhaps an ALSA problem. Could somebody help? Thanks and best regards, John

---

### Post by John_Rose1 on 2011-08-04
Hello,
This is apparently not a video card problem but rather a sound card problem.
When I added probe_mask=-1,0x2a to the line in /etc/modprobe.d/alsa-base.conf making it:
```

options snd-hda-intel model=dell probe_mask=-1,0x2a

```,
I get the following behaviour:
1. "normal" boots less than half the time as before"
2. the 45 second delay for delayed boots reduced to about 20 seconds (only 3 of the 7 probe codec errors).
I got this lead from [http://forum.xbmc.org/archive/index.php/t-98770.html](http://forum.xbmc.org/archive/index.php/t-98770.html) , I guess that if I modified the probe_mask further I could stop the other 4 probe codec errors?
                Best regards, John

---

### Post by John_Rose1 on 2011-08-04
Solved, if I use probe_mask=-1,0x0 [default handling of the integrated Intel sound card, probe no codecs for the discrete nVidia sound card (which I guess is part of the nVidia video card)], I get normal boots apparently all of the time. So this seems to have been related to the difficultly accessibe Dell discrete nVidia card.

Best regards,John

P.S. See [http://ubuntuforums.org/showpost.php?p=10465858&postcount=21](http://ubuntuforums.org/showpost.php?p=10465858&postcount=21) for a complete explanation of probe_mask parameter.

---

