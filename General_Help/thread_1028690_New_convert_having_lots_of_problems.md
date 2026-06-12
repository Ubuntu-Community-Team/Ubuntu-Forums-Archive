---
title: "New convert having lots of problems"
date: 2009-01-02
forum: General Help
---

### Post by jerrimaven on 2009-01-02
Hi everyone. Just a small introduction before I get to the point:

I'm fed up with Windows. I have a Windows machine at home, and a Mac at work. I decided to give Linux a try because my home computer is a Frankenstein. It gets replaced one part at a time. Windows wasn't cutting it, running incredibly slow. So I heard Linux worked great on older hardware and gave it a try.

Now, my problems. Linux has frozen up on me on several occasions. 3-4 times in a span of mere hours. Obviously, something must be wrong with my hardware or something. It happens at the most random times so I can't say one program in particular causes it. A couple times while downloading new software; a few times when only Firefox was running; once when I had an OpenOffice document open, etc.

I'm a complete Linux newb, so expecting me to know the very basics of Linux troubleshooting (or using the terminal for that fact) is not helpful :P

I have some issues with WINE playing games, but I'll leave that for another post, as I would like to get this problem resolved first.

Thanks in advance.

---

### Post by bgerlich on 2009-01-02
Be more specific, does the system just freeze with the last thing clearly visible, does it dump some info on the screen, did you do a clean install or WUBI install from windows, what computer are you using...

Also after a freeze try to check system logs (Administration-> System Log) and see if they provide some answer to what was happening right before a crash. The logs have time stamps, try to post the last thing in them before the crash (there will be some new entries that have apeared after you have rebooted, so follow the timestamps)

---

### Post by donkyhotay on 2009-01-02
A couple things first of all so that we can assist you. What kind of hardware do you have on your system (RAM, processor, etc.). Second what version of Ubuntu do you have (8.04-8.10? Ubuntu - Kubuntu?). Also how much does it freeze up? Does it freeze up just some of your applications? Everything but the mouse? Everything including the mouse? A few basic things to try is to run the software updater and make certain you have the latest kernel versions etc.

---

### Post by jerrimaven on 2009-01-02
Sorry, I guess I forgot that you guys can't see my desktop when it freezes :D

What happens is that none of the open windows can be moved around, or typed in, or used in any way. My mouse, however, can be moved freely. Like I said, I can't click on anything or use alt+tab.

I'll check my system log when I'm home and post it if I see anything fishy.

EDIT:
AMD quad-core, 2.6 ghz
4 gigs RAM
Western Digital Caviar 80 gig SATA 3.0 gb/s

Ubuntu 8.10

---

### Post by 2hot6ft2 on 2009-01-02
> **jerrimaven said:**
> 
AMD quad-core, 2.6 ghz
4 gigs RAM
Western Digital Caviar 80 gig SATA 3.0 gb/s

Ubuntu 8.10
Couple more questions about the specs so that it can be further narrowed down.
Video Card ?
Is the Video driver installed and active in System>Administration>Hardware Drivers?
Ubuntu 8.10 x86 32 bit or 64 bit?

---

### Post by exploder on 2009-01-02
You might try running the 64 bit version of Intrepid if you are not already because of the amount of RAM in your system. Also, try running memtest for a minute or two when you start up.I suggest this because i had similar problems and memtest revealed that one stick of RAM was bad.

---

### Post by stderr on 2009-01-02
When it freezes, are you able to switch to another TTY with (Ctrl + Alt + F1)? Are you able to restart the GUI with (Ctrl + Alt + Backspace)?

As a workaround (if you're having to resort to hard reboots) check out my page on [Magic Keys]("http://www.acepcs.co.uk/index.php?a=knowbase&kbs=linux&kba=magickeys") which may help you to reboot safely without risking filesystem corruption.

---

### Post by donkyhotay on 2009-01-02
Next time it happens I would try pushing ctrl-alt-f2 and see if that will pull up another terminal (ctrl-alt-f7 will put it back to the desktop). If you get a command prompt after pushing ctrl-alt-f2 then let us know and we'll help you look through your processes (don't be afraid of the CLI, we'll guide you through it). If pushing ctrl-alt-f2 doesn't do anything then I would start looking at hardware, especially RAM as mentioned previously. The installer disc has a memory test option available on it if thats what you need to do.

---

### Post by jerrimaven on 2009-01-04
The video card driver was not installed. I am in the process of installing it now. Obviously, I can't say if this has solved the freezing, but I'll let you know how it goes as far as tonight goes. Thanks!

---

### Post by jerrimaven on 2009-01-04
It crashed just now. Ctrl-alt-F2 did not work.

Here's the last few lines from the system log.

```

Jan  4 20:25:09 maven-desktop x-session-manager[5975]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout 
Jan  4 20:25:09 maven-desktop pulseaudio[6071]: module-x11-xsmp.c: X11 session manager not running.
Jan  4 20:25:09 maven-desktop pulseaudio[6071]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Jan  4 20:25:18 maven-desktop kernel: [   60.644099] NET: Registered protocol family 10
Jan  4 20:25:18 maven-desktop kernel: [   60.646175] lo: Disabled Privacy Extensions
Jan  4 20:25:19 maven-desktop avahi-daemon[5266]: Registering new address record for fe80::2e0:4dff:fea0:c8a9 on eth0.*.
Jan  4 20:25:28 maven-desktop kernel: [   71.065523] eth0: no IPv6 routers present
```

---

