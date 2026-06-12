---
title: "no sound makes me sad"
date: 2009-02-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by fencepost on 2009-02-21
I have a relatively new Dell Inspiron 1525 laptop which for the first few weeks ran without issue. I installed or upgraded something and now the sound won't work. 

I have spent many hours combing through similar posts, but to no avail, including these:
[http://linux.dell.com/wiki/index.php/Ubuntu_8.04#Known_Issues](http://linux.dell.com/wiki/index.php/Ubuntu_8.04#Known_Issues)
[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade)

I have also tried reinstalling every ALSA related package using the Package Manager. 

I'm relatively new to Linux but do have a minor clue. However, I need instructions for how to diagnose the problem as well as specific things to try. Here's what I know:

On a command line if I hit the backspace key I get a system beep - good stuff. 

When I hit the volume control on the top panel, the first time I get:
[INDENT]The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.[/INDENT]

The second time I get:
[INDENT]No volume control Gstreamer plugins and/or devices found. [/INDENT]

#uname -a
Linux ninegy-ninegy 2.6.24-23-generic #1 SMP Mon Jan 26 00:13:11 UTC 2009 i686 GNU/Linux

#speaker-test
speaker-test 1.0.15

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory

etc.

Any help is greatly appreciated...

---

### Post by florenciaalam on 2009-03-15
Hi, I have an inspiron 1420 ubuntu 8.04 and the same problem. 
My volume control icon is muted and when I click on it, it says:

> The volume control did not find any elements and/or devices to control.
This means either that you don't have the right GStreamer plugins installed,
or that you don't have a sound card configured.
You can remove the volume control from the panel by right-clicking the speaker
icon on the panel and selecting "Remove From Panel" from the menu.

and then just:

> No volume control GStreamer plugins and/or devices found.

I followed these instructions without success:

[http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/]("http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/")

I'm now downloading ubuntu 8.10 to see if it gets better.
I'm not an experienced ubuntu user. just a beginner.

Could you solve this problem?

thanks.

---

### Post by ezkl on 2009-03-29
I had the same issue after upgrading form 7.10 to 8.04 on a Dell inspiron 1420, after looking at several posts i solved the issue, it seems that some kernels have some issues with the alsa drivers.

What worked for me with kernel "2.6.24-22-generic" was this:

1. used Dmesg to look at the kernel messages, it showed that the integrated intel sound card had issues.

2. followed the instructions on this Dell Wiki ([http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade)) to update the Alsa drivers, i read that only doing this fixed the problem for some users ([http://ubuntuforums.org/showthread.php?t=948553&page=4](http://ubuntuforums.org/showthread.php?t=948553&page=4))

3. after i rebooted my laptop i updated the Alsa drivers as shown in this thread ([http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)), the only difference is that the only instruction used was sudo ./AlsaUpgrade-1.0.x-rev-1.16.sh -di, which downloads and installs the new alsa drivers.

4. reboot.

that fixed my problem, hope this fixes yours. :)

---

### Post by tomvietdungvn on 2009-03-30
i used ubuntu 8.10 for dell 1525.Sound is well.you can try

---

