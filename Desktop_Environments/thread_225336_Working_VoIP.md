---
title: "Working VoIP?"
date: 2006-07-29
forum: Desktop Environments
---

### Post by adam_kimber on 2006-07-29
Do any of you having VoIP working that is satisfactory and are able to make calls with clarity and ease and no problems?

I am struggling to get any program to work to a satisfactory level and it is fustrating me. :( 

I have the following problems:

Skype - Lots of echo, like talking in a tunnel. I did not have this problem with same version in Windows. 

Gizmo - works fine. Good audio quality but conversation drops off after about 5 minutes. This happens every five minutes, hang up and redial cures the problem only to get it back again after five mintues. The drop consists of a low hiss /hum instead of the voice of the other party. It can happen to either the caller or the reciever.

Ekiga - Sound drops out and sometimes crashes. But if i start Gizmo and then use Ekiga the sound is disabled and I can use the webcam and make a call. I called my friend for a few hours recently and the program did not die and worked fine with the video.

Wengo - The version that is in the repositories crashes after about 1 minute

I would like to use Gizmo as i like the interface and the sound quality is good and the program works. I have no idea what is causing these problems so i turn to you for help.

I hope the information below is some use too. 

$ uname -a
Linux esteban 2.6.15-26-k7 #1 SMP PREEMPT Mon Jul 17 20:36:04 UTC 2006 i686 GNU/Linux

$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:0a.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
0000:00:0e.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
0000:00:0e.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 0a)
0000:00:0f.0 Mass storage controller: Promise Technology, Inc. 20269 (rev 02)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] (rev a2)

---

### Post by Meck1982 on 2006-07-29
Hi,

I have been using skype first, but I started to search for alternatives, because skype did not use alsa and I wanted to phone while playing games like tremulous. So I tried Google Talk with Kopete, which was worse sound quality than skype imho. Wengo crashed and was unusable.
Yesterday I installed the new beta from Skype which uses alsa now and I am really happy, that there is no blocking audio any more.
I am not sure yet, but I think this new version has choppy audio sometimes.
So this is no real answer for your post, just some experiences... I whould suggest you to try the new Skype version or Google Talk.

---

### Post by clint1010 on 2006-07-31
I have been playing around with some VoIP services in ubuntu and have found Skype to work correctly for me out of the box, (used automatix to install). I also use teamspeak, works perfectly. However, i find that when i run teamspeak and configure the sound control, if i close it and run skype, my sound configuration changes automaticly. I have to re-set it to run teamspeak again. To eliminate echoing, make sure the speaker icon is crossed out for the mic on the "Capture" tab in Gnome->Volume control

---

### Post by Meck1982 on 2006-07-31
So which version of skype did automatix install? 1.3.0? And did you select alsa? Are you able to listen to music while skyping? Skype with oss also works for me with good sound quality, but it blocks the whole sound output, which means I am not able to listen to music while skyping.

---

