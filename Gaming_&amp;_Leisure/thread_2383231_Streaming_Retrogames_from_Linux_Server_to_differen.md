---
title: "Streaming Retrogames from Linux Server to different Clients"
date: 2018-01-22
forum: Gaming &amp; Leisure
---

### Post by dominik96 on 2018-01-22
Hello !

My name is Dominik and i'm a student (but my question is not related to it). What I want to do is "in home streaming" of retrogames. I kind of like the idea because I already a have a server running and I don't want to use an raspberry pi therefore (and I only have RPI v1).

My Server is a new HP Gen 10 Microserver with 8GB of RAM, 2x4TB HD's and an 512GB SSD. It should have enough power to run some emulations, because the RPI v3 can handle this task too. But I want to stream the games for example to a Fire TV Stick or to other PC's. On the Microserver I use Ubuntu Server (headless), with the latest LTS version installed. The best option for retro games seems to be RetroArch. Can this be streamed to other devices + Inputs streamed back for controlling the games? Basically the same way Moonlight Stream works (but of cause without an NVIDIA graphics card). The most imporant client would be the Amazon Fire TV Stick. 

Thanks in advance,
Dominik

---

### Post by TheFu on 2018-01-23
I don't have an answer. I do have a process you can follow in search of a solution, however:

I think the question is more about what a Fire stick can support than anything else.  Make a list of all the ways it can receive remote windows, programs, desktops, streams, then start working your way through trying to send those from your Linux systems.

Common ways for Linux to do this are:
* X11 forwarding
* VNC / other VNC protocols
* x2go / other NX protocols
* Spice (requires a virtual machine) using QXL drivers
* RDP / the MSFT protocol
* WebRTC stuff.  My Nextcloud server has this, but the Android client isn't working for me.
* MiraCast - only for streaming media, not desktops; [https://askubuntu.com/questions/318298/ubuntu-as-miracast-sender-receiver](https://askubuntu.com/questions/318298/ubuntu-as-miracast-sender-receiver)
* and a number of web-based remote desktop things.  

But the FireStick will be the most limited.  Linux/Ubuntu will have some limitations, since proprietary tools are often not ported to run on Linux.

I've heard of nvidia-Moonlight. Never seen it because I only have nVidia cards that don't support it and don't have Windows.

I tried getting X11 forwarding to work last night.  Found an Android X/Server, but couldn't get an X/Client to connect to it.
Also tried the NoMachine NX client on Android, but my NX servers (not NoMachine) didn't work. I use x2go, daily, constantly, now. It is a nice solution for remote desktops, especially for headless systems.
I've tried VNC in the past. It is slow.
Looked up Miracast. Didn't get any farther.

Good luck.

---

