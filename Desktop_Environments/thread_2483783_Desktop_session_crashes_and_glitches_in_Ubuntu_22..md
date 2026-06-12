---
title: "Desktop session crashes and glitches in Ubuntu 22.04"
date: 2023-02-08
forum: Desktop Environments
---

### Post by yurad on 2023-02-08
I have been using Ubuntu on my Asus X556UQ laptop since 2017. However, my current 22.04 version is unreliable due to various desktop session crashes and various glitches. Session crashes happen every day or two. I'm running into desktop crashes with Gnome on Xorg and Wayland as well as KDE Plazma so it's not specific to gnome-shell. I've attached the log of the latest Gnome on Xorg crash from January 31st. [ATTACH]291734[/ATTACH] I can see that at 16:04 I paused the laptop (by closing the lid). At 18:29 I resumed the session. Around 18:40 Gnome crashed. I'm not very familiar with Linux components and can't figure out in the logs what could be the root cause of these crashes.
(I see in the log that plasma-xdg-desktop-portal-kde.service is running. Should it run on Gnome? )
I am adding more information. My Ubuntu became unreliable after upgrading to 21.10. Before that, all my problems with Ubuntu were solvable. I've always worked in Ubuntu and only booted into Windows for certain tasks. After updating to 21.10, 8GB of memory became critically small, although my workload did not change. Each switch between windows gave a pop-up message "The program is not responding." There were constant delays in UI responses. I tried KDE. However, KDE did not improve stability. Thus, I had to switch to Windows as the main OS on this laptop. In August I finally decided to upgrade to 22.04. Overall performance on 22.04  looks much better. But session crashes and various glitches make my Ubuntu unreliable.
I will give one example of glitches. Recently, in the middle of work, my snap Firefox lost access to my home directory. It was stressful because I couldn't continue with my work. I then found a quick workaround. After work, I saw in the log that the problem was with xdg-desktop-portal. After Gnome session restart the access was restored. However, I can't let Firefox lose access to my directories. ( If I fix the GNOME and KDE crashes, I will revert to the deb package Firefox. )
The last thing I want to mention is my feeling that Firefox on my Ubuntu requires 30% to 50% more resources than on my Windows 10. This slows down the system. I did not have the opportunity for systematic tests. But by doing more or less the same job every day, it's easy to notice the time it takes to do the same amount of work. Also, when I listen to music while I'm working, the audio stream is quite stable on Windows, while on Ubuntu it often breaks.
Please give me advice on how to investigate my problems

---

### Post by ActionParsnip on 2023-02-10
Have you tested your RAM health? This will be a good start

---

### Post by yurad on 2023-02-11
I didn't run a RAM test just because Windows 10 runs on the same laptop without issue. I've been on Windows for about 3 weeks and I don't see any issues. No slowness, no delays. I just got stuck with the screen saver one day. I couldn't get the password prompt.
Anyway, I ran RAM tests now. Because I didn't find memtest in the GRUB menu anymore, I ran memtester in the Virtual terminal. Everything looks ok. I have attached the output. [ATTACH]291752[/ATTACH]

After it, I switched to Windows and ran the Windows Memory Diagnostics Tool. The result is "The Windows Memory Diagnostic tested the computer's memory and detected no errors"
So, I assume that my RAM is ok.

---

### Post by yurad on 2023-03-14
I hope I solved my old problem. Since Windows 10 works well on my laptop, I figured the Ubuntu issue was a setting, most likely a driver setting. My laptop has dual video, Intel HD Graphics 520 and NVIDIA GeForce 940MX. I made only two changes: in the NVIDEO X server settings and, at the same time, I disabled hardware acceleration in Firefox.
Since then, there have been no more  GUI crashes. Now Ubuntu works just as well as Windows. It was most likely a bug between the NVIDEO driver and my BIOS.

---

