---
title: "Nvidia card no longer being used after bios update"
date: 2024-11-07
forum: Gaming &amp; Leisure
---

### Post by jorritTyb on 2024-11-07
[COLOR=#111111][FONT=Arial]So I have an MSI Raider GE76 laptop with an RTX 3080. This has always worked fine. A few days ago I bought a Philip ultrawide screen and connected that using the thunderbolt connector. That also worked and I could use accelarated graphics on it. But today my screen decided to not connect anymore (while it still worked for my other windows laptop). I found out that a bios update might fix this and indeed it did! The screen is now working again. However, after the bios update it seems that applications no longer use the nvidia card. This is with Kubuntu 24.04

Here some diagnostics:[/FONT][/COLOR]

[COLOR=#111111][FONT=Arial]> prime-select query[/FONT][/COLOR]
[COLOR=#111111][FONT=Arial]nvidia

[/FONT][/COLOR][COLOR=#111111][FONT=Arial]> &#8203;ubuntu-drivers devices[/FONT][/COLOR]

```
[COLOR=#111111][FONT=Arial]*== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==*[/FONT][/COLOR]
[COLOR=#111111][FONT=Arial]*modalias : pci:v000010DEd0000249Csv00001462sd00001305bc03sc00 i00*[/FONT][/COLOR]
[COLOR=#111111][FONT=Arial]*vendor : NVIDIA Corporation*[/FONT][/COLOR]
[COLOR=#111111][FONT=Arial]*model : GA104M [GeForce RTX 3080 Mobile / Max-Q 8GB/16GB]*[/FONT][/COLOR]
[COLOR=#111111][FONT=Arial]*driver : nvidia-driver-535 - distro non-free*[/FONT][/COLOR]
[COLOR=#111111][FONT=Arial]*driver : nvidia-driver-535-open - distro non-free*[/FONT][/COLOR]
[COLOR=#111111][FONT=Arial]*driver : nvidia-driver-550 - distro non-free recommended*[/FONT][/COLOR]
[COLOR=#111111][FONT=Arial]*driver : nvidia-driver-470 - distro non-free*[/FONT][/COLOR]
[COLOR=#111111][FONT=Arial]*driver : nvidia-driver-470-server - distro non-free*[/FONT][/COLOR]
[COLOR=#111111][FONT=Arial]*driver : nvidia-driver-535-server-open - distro non-free*[/FONT][/COLOR]
[COLOR=#111111][FONT=Arial]*driver : nvidia-driver-550-open - distro non-free*[/FONT][/COLOR]
[COLOR=#111111][FONT=Arial]*driver : nvidia-driver-535-server - distro non-free*[/FONT][/COLOR]
[COLOR=#111111][FONT=Arial]*driver : xserver-xorg-video-nouveau - distro free builtin*[/FONT][/COLOR]

```
[COLOR=#111111][FONT=Arial]> software-properties-gtk
[/FONT][/COLOR][IMG]https://i.imgur.com/LkMDScW.png[/IMG]

[COLOR=#111111][FONT=Arial]So all this looks ok. Nevertheless games which were previously using nvidia (before the bios update) now use Intel Graphics instead (like Minecraft and Vintage Story).[/FONT][/COLOR]

Here is a link to the full dmesg output: [https://gist.github.com/McJty/f3d202466aa17eba5d62eac59b68e1a9](https://gist.github.com/McJty/f3d202466aa17eba5d62eac59b68e1a9)

[COLOR=#111111][FONT=inherit]Any clues?

Thanks in advance,&#8203;[/FONT][/COLOR]



[COLOR=#111111][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#111111][FONT=Arial]
[/FONT][/COLOR]

---

### Post by Shishimaru on 2024-11-07
Hi, if you have access to a Windows system from that laptop, can you double check that the Nvidia card is working correctly when using the thunderbolt port?

Also, open the MSI Center and double check that the hybrid graphics mode is being used instead of the Intel one. Unfortunately, on my MSI laptop I cannot change this in the BIOS as the option is grayed out, so the Windows' app must be used. And it's even a terrible app in my opinion, but however.

Also, try to see if you can launch your games with this command or option: DRI_PRIME=1 

For example, you can launch directly Steam with DRI_PRIME=1 steam or just use the same option for each game by right clicking it in the library and then setting it. This command should launch the app/game by using Nvidia GPU.

In the end, you can also try to reinstall the drivers again. Switch to Nouveau, reboot, switch to Nvidia, reboot. Just leave this as a last resort though. It should be safe, but Nvidia drivers likes to play games, and not good ones. 

Ubuntu has a quick option to launch an app with the discrete GPU, but not Kubuntu.

---

### Post by jorritTyb on 2024-11-07
I actually solved it by disabling Secure Boot. This was disabled before but updating the bios apparently reset it. Thanks for the other tips though

---

