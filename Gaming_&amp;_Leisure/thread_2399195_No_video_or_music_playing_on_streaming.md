---
title: "No video or music playing on streaming"
date: 2018-08-22
forum: Gaming &amp; Leisure
---

### Post by anro29 on 2018-08-22
Hello there,
First of all, I am sorry if this thread is in the wrong place (first time using this forum).

I have yesterday installed on my laptop (asus E200H) Ubuntu 18.04 and I got a few problems with it. One of them is I can't see a youtube video, a twitch stream or listen to deezer.
On youtube, the video seems to try loading, but never actually starts playing. On twitch it looks like a mute slideshow. Deezer is just silent (even though firefox displays it as making sound).

On the other hand, VLC works fine reading videos on a USB key, and mp3s are played without any trouble. As this computer's duty is to play streaming (and a bit of texxt editing, but about 95% of usage is streaming), it is a bit of a problem.

Result of lspci command : (if it helps).
> 00:00.0 Host bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SoC Transaction Register (rev 36)
00:02.0 VGA compatible controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Configuration Registers (rev 36)
00:0b.0 Signal processing controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Power Management Controller (rev 36)
00:14.0 USB controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series USB xHCI Controller (rev 36)
00:1a.0 Encryption controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Trusted Execution Engine (rev 36)
00:1c.0 PCI bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Express Port #1 (rev 36)
00:1f.0 ISA bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCU (rev 36)
01:00.0 Network controller: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter (rev 31)



Thanks for reading, and sorry for any mistake

---

### Post by TheFu on 2018-08-22
Try a different browser, like chromium.   I've always had issues with firefox and media. It has been worse since they switched to using PulseAudio from ALSA, IMHO.

---

