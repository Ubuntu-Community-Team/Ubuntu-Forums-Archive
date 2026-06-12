---
title: "Remote Desktop/VNC for teaching?"
date: 2022-11-05
forum: Desktop Environments
---

### Post by imWACC0 on 2022-11-05
I have set up a small home computer lab for my grandchildren... 3 or 4 PC, and a DD-WRT router. They have 300mb cable ISP (sorry, I don't know the up speed). I have 500mb asymmetrical fiber.

I live an hour and a half away, but want to teach them Linux. Also maintain the network/lab. That means I can visit a few times a month, but would like to be able to take charge of the system, do stuff on the PC, and have them see how/what I'm doing. Also, do a rotating schedule of the three, for other type teaching.

[https://alternativeto.net/](https://alternativeto.net/) has 60+ alternative listings, but I don't want to hand over money for this project. Just Open Source is 20+.

Anyone done this? Or know of a good program that will let me work *WITH* the kids?

---

### Post by TheFu on 2022-11-05
> **imWACC0 said:**
>  
Anyone done this? Or know of a good program that will let me work *WITH* the kids?

It depends on what you want to teach.  For sharing your desktop, you can use the free service from Jitsi - meet.jit.si.  Point a webrtc-capable web browser at an agreed random URL below there. It will create a room for you to use for a few hours.  You can reuse the same room day after day.  The best browser is Chromium, but firefox and others are reported to work. Each is a little different.  Also, if the systems don't have a headphone setup, the feedback from microphones in the same room will be terrible.  One at a time, and it will be ok.  Jitsi Meet is what my LUG has been using for years to meet - even before COVID.

For text training, use ssh.  No question.  Then you can ssh into each of their systems (use a different port with the router forwarding to it for the specific LAN IP.  Just be certain to setup strong authentication and block 99+% of the internet from access.  You can setup the connection on your side, then have the kids ssh into your system and work together.  [https://unix.stackexchange.com/questions/2523/what-are-other-ways-to-share-a-tmux-session-between-two-users](https://unix.stackexchange.com/questions/2523/what-are-other-ways-to-share-a-tmux-session-between-two-users)  ssh with either tmux or screen are the options for sharing sessions.  [https://www.webservertalk.com/linux-screen-command](https://www.webservertalk.com/linux-screen-command)

For remote control, really the only tool that I'd trust is x2g0.  It is based on ssh too.  So you'll need to setup ssh regardless.  x2go is how a Linux conference here has presenters show their screens for the recording and screaming system.  [https://wiki.x2go.org/doku.php/doc:installation:desktop-sharing](https://wiki.x2go.org/doku.php/doc:installation:desktop-sharing)

If the solution doesn't use ssh, I think it is a security failure.  Don't use VNC or RDP.  Just don't.  
If you setup full VPN connections between the two LANs, then security is handled and invisible.  This is probably beyond the ability of most Linux end-users, however.  [https://cosmicpercolator.com/2020/04/06/lan-to-lan-vpn-using-wireguard/](https://cosmicpercolator.com/2020/04/06/lan-to-lan-vpn-using-wireguard/) Appear to be reasonable instructions for intermediate-level network+linux people, but I didn't try this myself.

---

### Post by imWACC0 on 2022-11-05
> **TheFu said:**
> It depends on what you want to teach. 

For remote control, really the only tool that I'd trust is x2g0.  It is based on ssh too.  So you'll need to setup ssh regardless.  x2go is how a Linux conference here has presenters show their screens for the recording and screaming system.  [https://wiki.x2go.org/doku.php/doc:installation:desktop-sharing](https://wiki.x2go.org/doku.php/doc:installation:desktop-sharing)

Yes, full sharing. I want to teach all aspects of computing: Programing, Networking, Security... If it's on a CompTIA A+ test, I want them to have at least some knowledge of it.

Also want to do stuff with Physics, but most of that's going to be IRL

I'll get x2g0, only hint I've had so far

---

### Post by ActionParsnip on 2022-11-06
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-22-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-22-04)

---

### Post by imWACC0 on 2022-11-06
> **ActionParsnip said:**
> [https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-22-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-22-04)

Will TightVNC allow me to show them what I'm doing? I know how to SSH into the system, but I can't show what I'm doing.
Also, seeing as there 6, 8, and 11 years old, I may have to do GUI until they can learn to type **and** know the logic/funny spelling of command line.

---

### Post by ActionParsnip on 2022-11-06
> **imWACC0 said:**
> Will TightVNC allow me to show them what I'm doing? I know how to SSH into the system, but I can't show what I'm doing.
Also, seeing as there 6, 8, and 11 years old, I may have to do GUI until they can learn to type **and** know the logic/funny spelling of command line.

Try it. See what works

---

### Post by TheFu on 2022-11-06
> **imWACC0 said:**
>  Also, seeing as there 6, 8, and 11 years old, I may have to do GUI until they can learn to type **and** know the logic/funny spelling of command line.

There's something to be said about NOT providing any GUI for the kids, to start.  Keeping the environment very simple let's them explore with things that are easy to understand.  
[https://lifehacker.com/i-raised-my-kids-on-the-command-line-and-they-love-it-5974087](https://lifehacker.com/i-raised-my-kids-on-the-command-line-and-they-love-it-5974087) - a gui who taught his kids Linux using only the shell.
[https://www.youtube.com/watch?v=bddM-JyNuXs](https://www.youtube.com/watch?v=bddM-JyNuXs) - an educational Linux distro without any GUI.

Don't underestimate their abilities.

---

### Post by imWACC0 on 2022-11-06
> **TheFu said:**
> There's something to be said about NOT providing any GUI for the kids, to start.  Keeping the environment very simple let's them explore with things that are easy to understand.  
[https://lifehacker.com/i-raised-my-kids-on-the-command-line-and-they-love-it-5974087](https://lifehacker.com/i-raised-my-kids-on-the-command-line-and-they-love-it-5974087) - a gui who taught his kids Linux using only the shell.
[https://www.youtube.com/watch?v=bddM-JyNuXs](https://www.youtube.com/watch?v=bddM-JyNuXs) - an educational Linux distro without any GUI.

Don't underestimate their abilities.

Thanks for the links, too much to do today... I'll read when I get home and use it in my teaching

Still have to build a desk for a 60cm x 168cm spot, get two PC set up on it.

---

