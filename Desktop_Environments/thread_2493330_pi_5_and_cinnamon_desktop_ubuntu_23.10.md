---
title: "pi 5 and cinnamon desktop ubuntu 23.10"
date: 2023-12-11
forum: Desktop Environments
---

### Post by marie91 on 2023-12-11
I've been trying to install cinnamon desktop on my new pi 5 using Ubuntu 23.10. It downloads and installs no problem that I can see. I log out, then on the login screen, I click on the settings icon, then select cinnamon and hit enter. The screen blanks out then comes back to the logon. I've tried the cinnamon, cinnamon software rendering, will not open. The only one that works is the Ubuntu selection. Any ideas? Cinnamon work on my pi 4 no problem.
Thanks in advance

---

### Post by TheFu on 2023-12-12
I hope Santa brings me a Pi5.

My only guess is to try using Xorg, not Wayland. Choose this before login, use the "Gear" to make the selection.

---

### Post by marie91 on 2024-01-07
I tried Xorg still the same thing. It seams your stuck with whatever desktop the distro comes with.

---

### Post by TheFu on 2024-01-07
> **marie91 said:**
> I tried Xorg still the same thing. It seams your stuck with whatever desktop the distro comes with.

Santa did bring a Pi5 here with some other toys.  I haven't taken the time to put it together and set it up yet.  Seems the pi4 is better for my intended use (video playback device) than the Pi5 due to h.264 support in hardware. The pi5 uses software to decode h.264 - meh.

Full day of stuff to be done already, but I'll try to do what you are trying later today.  
[https://cdimage.ubuntu.com/releases/23.10/release/ubuntu-23.10-preinstalled-desktop-arm64+raspi.img.xz](https://cdimage.ubuntu.com/releases/23.10/release/ubuntu-23.10-preinstalled-desktop-arm64+raspi.img.xz) is the image.  Requires at least 4GB of RAM. I'll use cp to place the image onto the microSD card after decompressing it.  I have an external USB3 (USBc connector) SSD somewhere that could be used for this, but I'll try with just a microSD first.  For a desktop, the SSD route would be smarter ... or a SATA disk.  

After the bloated Gnome desktop is up, then I'll install **ubuntu-mate-desktop** followed by cinnamon.  The Gnome DE uses a funky login manager that can be a problem for other DEs.  I much prefer almost any other login manager.

---

### Post by #&amp;thj^% on 2024-01-07
> **marie91 said:**
> I've been trying to install cinnamon desktop on my new pi 5 using Ubuntu 23.10. It downloads and installs no problem that I can see. I log out, then on the login screen, I click on the settings icon, then select cinnamon and hit enter. The screen blanks out then comes back to the logon. I've tried the cinnamon, cinnamon software rendering, will not open. The only one that works is the Ubuntu selection. Any ideas? Cinnamon work on my pi 4 no problem.
Thanks in advance

This is the third pi 5 fail on cinnamon i've seen in the past couple of weeks.
This is just *Me* but I sent my pi5 back just not suited for my usage.
And i agree with TheFu video is much better on the pi4.
I am curious to see how TheFu rates it. I'm sure he is much kinder than me. :)

---

### Post by TheFu on 2024-01-07
> **1fallen said:**
> This is the third pi 5 fail on cinnamon i've seen in the past couple of weeks.
This is just *Me* but I sent my pi5 back just not suited for my usage.
And i agree with TheFu video is much better on the pi4.
I am curious to see how TheFu rates it. I'm sure he is much kinder than me. :)

I don't plan to use the pi5 for video, since nearly all my content is in h.264, but until my media distro supports the pi5 hardware, I cannot test.

It is only recent that I've have even a pi4 and could play h.265 stuff at all. My pi2 and pi3 systems run h.264 with hardware support really well. I have a license for hardware support of MPEG2 content on the pi2, and that works. On the pi3, the software decoder works - it is powerful enough. I don't have much hidef mpeg2 - just recent, watch-once, recordings.  Even then, I'll usually transcode to h.264 which is handled in hardware on all the devices.

My pi4 fan is really loud, so I need to solve that problem.  The pi5 fan is supposed to only turn on when needed.  That is yet to be seen, by me.

Just to be clear, I don't have any media local to any raspberry pi systems and only use wired connections, never wifi.  All media is streamed from a Jellyfin server.

---

