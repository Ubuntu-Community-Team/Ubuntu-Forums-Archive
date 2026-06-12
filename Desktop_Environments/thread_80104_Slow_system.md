---
title: "Slow system"
date: 2005-10-21
forum: Desktop Environments
---

### Post by whiskas on 2005-10-21
Hello everyone,
This is my first post, so please be gentle :)
I'm running a freshly-installed Breezy, all updates applied, no applications installed but the default ones, and I'm experiencing a **very** annoying problem: my whole desktop feels extremely slow.
First, the specs, then some examples:
Ahtlon XP 1700+ running on a KT400 chipset (Gigabyte motherboard), with 768MB RAM, and some ATI Radeon 9250 video card. Storage is provided by a WD Caviard 80GB HDD (8MB cache - JB series). Hardware wise, everything seems to be smooth and silky - no problems whatsoever, even 3D acceleration (fglrx driver) works like a charm.
The problem is that 2D operations feel very, very slow. Not only that they feel so, but I am very confident that they actualy are. For example: switching between windows (ALT-TAB) takes about 1 second, and window redrawing is **painfully** slow (I can definitely see it beeing redrawn). In terms of pure performance, I can see no problems, but the general desktop feel is that it's waaaay slow.
I'm no GNU Linux newbie, I've tried some tweaks, installed the k7 kernel and assorted modules, disabled some services, but there is absolutely no improvement.
I'm very, very open to suggestions, and if you feel inclined to, please do ask for more info, as I'm more than glad to provide it.
Thanks a bunch, and have a happy weekend :)

P. S. I've also checked the logs, I can find no problems whatsoever.

---

### Post by bvc on 2005-10-22
Others disagree, or say they have no issues, but I did and found that a newer version of cairo than 1.0.0 (slow aa font rendering) fixed the prob. I know it was this because it is the only change I made to get my speed back. I have a cvs version but the latest is 1.0.2.

---

### Post by whiskas on 2005-10-22
[QUOTE=bvc]Others disagree, or say they have no issues, but I did and found that a newer version of cairo than 1.0.0 (slow aa font rendering) fixed the prob. I know it was this because it is the only change I made to get my speed back. I have a cvs version but the latest is 1.0.2.[/QUOTE]
I just checked it out, and I have version 1.0.2 installed, as well.
Any other ideas? :o

---

### Post by bvc on 2005-10-22
oh, looky there...I have 1.0.2 as well. Wonder when that happened? :???: 

No other ideas here. I have nvidia but I've seen a few ati threads. Maybe there's something useful in them?

---

### Post by iMerlin on 2005-10-22
I'm running two Breezy installations. Both upgraded from Hoary.

Sometimes (usually when running Firefox or other text intensive programs) the Xorg process goes to 50-80% cpu until I shut the application down.

This makes the whole system slow as hell. I have no idea why this is happening, tried replacing my video driver without luck.

Cairo font rendering? Is any of that configurable?

---

### Post by mediocrates on 2005-10-22
[QUOTE=whiskas]I can see no problems, but the general desktop feel is that it's waaaay slow.[/QUOTE]

The custom build of Firefox that comes with Ubuntu seems to be part of the problem. You cannot uninstall it as about half the system depends on it but you can install the *real* version of Firefox in a different directory (I used /usr/local/firefox) and set it up as the default browser - change "firefox %u" to "/usr/local/firefox/firefox %u" in the properties for the Firefox menu entry and any  desktop or panel shortcuts you've set up. Also change this in Preffered Applications. You should be able to copy any plugins from /usr/lib/mozilla-firefox/plugins to /usr/local/firefox/plugins.

You'll need to install libstdc++5 before installing Firefox.

You can probably lower the default swappiness value for the kernel too.

Open a terminal and type "sudo cat /proc/sys/vm/swappiness" (without quotes) to see what the current value is. The default is 60, to change it to 10 enter "sudo sysctl -w vm.swappiness=10" at the command line. This works wel on my system, a 950MHZ Duron with 1GB of RAM.

Once you fins a value you like you'll need to edit the /etc/sysctl.conf file to use that value every time you boot the PC. Run the command "sudo gedit /etc/sysctl.conf" at the command line and add the line vm.swappiness=10 to it.

---

### Post by bvc on 2005-10-22
[QUOTE=iMerlin]I'm running two Breezy installations. Both upgraded from Hoary.

Sometimes (usually when running Firefox or other text intensive programs) the Xorg process goes to 50-80% cpu until I shut the application down.

This makes the whole system slow as hell. I have no idea why this is happening, tried replacing my video driver without luck.

Cairo font rendering? Is any of that configurable?[/QUOTE]Not that I'm aware of. Could be other aspects of cairo or even something else. I know I saw a big diff past version 1.0.0. As an nvidia owner I know setting ```
Option 		"RenderAccel" 		"true"
```in xorg.conf locks the sys and was working fine before the implementation of cairo. It speeds up aa font rendering but now can not be utilized.

I still notice a diff in speed, or rather, rendering of windows is slow. People are reporting this with the latest nvidia driver thinking it is to blame but I still have the old version.

---

### Post by whiskas on 2005-10-22
[QUOTE=mediocrates]The custom build of Firefox that comes with Ubuntu seems to be part of the problem. You cannot uninstall it as about half the system depends on it but you can install the *real* version of Firefox in a different directory (I used /usr/local/firefox) and set it up as the default browser - change "firefox %u" to "/usr/local/firefox/firefox %u" in the properties for the Firefox menu entry and any  desktop or panel shortcuts you've set up. Also change this in Preffered Applications. You should be able to copy any plugins from /usr/lib/mozilla-firefox/plugins to /usr/local/firefox/plugins.

You'll need to install libstdc++5 before installing Firefox.

You can probably lower the default swappiness value for the kernel too.

Open a terminal and type "sudo cat /proc/sys/vm/swappiness" (without quotes) to see what the current value is. The default is 60, to change it to 10 enter "sudo sysctl -w vm.swappiness=10" at the command line. This works wel on my system, a 950MHZ Duron with 1GB of RAM.

Once you fins a value you like you'll need to edit the /etc/sysctl.conf file to use that value every time you boot the PC. Run the command "sudo gedit /etc/sysctl.conf" at the command line and add the line vm.swappiness=10 to it.[/QUOTE]
After further experimentation, it seems that **Mozilla Firefox** is, indeed, part of the problem. What is so different / special in the Ubuntu build that makes it so slow?
In regard to swappinnes, I have recently upgraded to 1GB of RAM, but even before, the swap wasn't touched at all, even when running full blown (browser, music player, several Nautilus windows, gaim, GIMP, etc. etc.).
Thing is, this problem is making me nuts! I've tried so hard to stay away from the dark side (read: Windows), but you know what? This might just do it... :???:

---

### Post by mediocrates on 2005-10-22
[QUOTE=whiskas]After further experimentation, it seems that **Mozilla Firefox** is, indeed, part of the problem. What is so different / special in the Ubuntu build that makes it so slow?[/QUOTE]

I think somebody screwed up but this is just my opinion.

Turning IPv6 off is also a good idea. Type about:config in the address bar and look for network.dns.disableIPv6 and set the value to true.

> In regard to swappinnes, I have recently upgraded to 1GB of RAM, but even before, the swap wasn't touched at all, even when running full blown (browser, music player, several Nautilus windows, gaim, GIMP, etc. etc.).

My bad, it's kernel swapping, not general swapping. Even if you've got a lot of RAM the kernel will routinely swap bits of itself to disk. The default is to swap more than necessary for a lot of people.

---

### Post by bvc on 2005-10-22
#Firefox: about:config> network.dns.disableIPv6 -> true
network.http.pipelining -> true
network.http.pipelining.maxrequests -> 8
network.http.proxy.pipelining -> true

---

### Post by rjwood on 2005-10-22
which kernel are you using?

---

### Post by whiskas on 2005-10-22
It's not Firefox network performance that's bothering me. After all, I'm sitting on a 100Mbit pipe, and pages do load very quick. It's the 2D / drawing / rendering performance that's driving me crazy. Even the menus are so slow, I can actually see them being drawn!
And I've tried both the stock kernel (i386), and the k7 optimized one. Still no difference...

---

### Post by rjwood on 2005-10-22
you may want to check this out:

[Performance - Ubuntu Forums]("showthread.php?t=71680")

I hope this helps

---

