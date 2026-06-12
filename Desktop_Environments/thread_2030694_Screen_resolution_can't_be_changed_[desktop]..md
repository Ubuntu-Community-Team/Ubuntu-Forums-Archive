---
title: "Screen resolution can't be changed [desktop]."
date: 2012-07-20
forum: Desktop Environments
---

### Post by zontar on 2012-07-20
Hello,

I've been unsing Ubuntu for a few years now.
I was very very happy running 10.10 - everything seemed to work with very little futzing around, and it really had me sold on Ubuntu as my preferred flavour of Linux for a desktop environment. Debian is rock-solid, and I use it for my headless servers, but it's a bit too restrictive for my tastes in a desktop system.

I've decided to try and put together a new media server [DLNA]  to work with some new A/V gear that advertises DLNA compatibility [I am trying serviio but this may change], So I see that 12.04 LTS is the latest version of Ubuntu.

Alas... It's been nothing but trouble and hair-pulling from the start. It refused to install from either the server or desktop CD - always hung at one of the keyboard screens - spent 4 days trying this. I was FINALLY able to get the installer running with the "alternate" CD and diabling some options [ACPI if I recall or something like that]. When I installed 10.10 it took 15 minuted to have a running system.

So the system is running, but there have been so many changes since 10.10 that I am having MAJOR problems with even the simplest things - like the lack of an xorg.conf file - I can't get the screen resolution on the desktop to change and stick. I have literally tried a hundred different methods, many of which apparently worked for previous releases but no longer do. I am getting really frustrated and am tempted to revert to 10.10 just because I know it worked well.

Maybe it's just me and the particular system I'm trying to run this on [a Dell Optiplex G240 - a very common and reasonably capable box in its day]. It just seems that many changes were made that make no sense to me whatsoever [and I HATE the new desktop menu thing - I can never seem to find ANYTHING without a search - hardly productive].

I know that right now I'm tired and cranky, but I'm ready to pack 12.04 in - it's too much trouble and after a month I STILL cannot get my desktop screen to 1280x1024 @ 75.00Hz - it's stuck @60.00Hz and the right edge is black space and the ledft edge is cutoff. It's just a common old Dell 17" CRT  with a VGA cable. Nothing exotic or cutting edge. Even the login screen is malformed this way and the console during boot is cutting off text on the left edge.

[...And don't get me started on SAMBA, which [I know - off topic on this forum] I had setup under 10.10 in 5 minutes, and I cannot get to work at all in 12.04...]

So can somebody point me towards some possible CURRENT solutions [the display wiki is no longer valid for 12.04 - none of the presented solution apply].
I have tried adding an entry in usr/share/X11 someplace that I can't recall, adding a startup script with xrandr strings, and adding an entry in my .profile all to no avail. Oh, and instructions for generating an xorg.conf file all fail with errors regarding gdm not being a service [again, probably outdated guides that do not apply to c=some differences in 12.04]. The "Display" applet does not even allow setting a rate - this is pretty lame, as it's not properly detecting my monitor.

So please help restore my faith in Ubuntu - it's starting to look very broken and that 12.04 is to Ubuntu what Vista was to Windows. Sorry to prattle on so, but this has been building up for weeks :(

---

