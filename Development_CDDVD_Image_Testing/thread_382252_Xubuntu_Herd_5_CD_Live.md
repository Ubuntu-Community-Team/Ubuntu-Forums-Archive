---
title: "Xubuntu Herd 5 CD Live"
date: 2007-03-11
forum: Development CD/DVD Image Testing
---

### Post by jerrylamos on 2007-03-11
- Booted CD Live  Xubuntu Herd 5 on 1.07 GHZ Celeron O.K.  Phillips LCD runs 1024x768 default resolution.
- Firefox access internet O.K., because Xubuntu didn't have Network Manager.  Feisty Ubuntu and Kubuntu Network Manager disable already functioning eth0 reason "no carrier detect"?  I have to manually enable eth0 on Herd 5 Ubuntu and Kubuntu. Xubuntu Herd 5 ran fine as booted.
- Firefox ran AOL Mail fine.  Herd 5 Kubuntu Konqueror won't.
- Persistent didn't work on Xubuntu; it's been busted on Feisty since about 20070210.  Edgy Xubuntu persistent does work I just re-checked with same hardware.  I assume Herd 5 Xubuntu has same problem as Herd 5 Ubuntu with persistent.  There's a launchpad bug on this.
- On 2 GHZ Pentium 4 with 17" LCD Xubuntu booted up in 1024x768.  It should have come up 2048x1024x24, which is how it boots with PCLinuxOS, Simply Mepis, even little (90MB iso) Puppy Linux.  I entered a bug on Launchpad on Feisty Ubuntu, I assume Xubuntu uses same monitor detection code.
- Xubuntu Shared folder loaded SMB O.K.  Dapper didn't pick it up on "places", "network servers" however "connect to server" and manually key in the address worked O.K.  "connect to server" "browse..." also found it.
- I don't know how to access Dapper on the LAN from Xubuntu, ftp I presume since Xubuntu doesn't seem to have Places, Network Servers?  I got "connection refused" when I tried to ftp to Dapper from Xubuntu.  I don't know enough linux line commands yet.  There are 5 computers on our LAN and we frequently ship pictures and other files around.
Cheers, Jerry

---

### Post by obocho on 2007-03-12
hi,   I also tried to use xubuntu on my inspiron 8600i, but I couldn't make it work with 1680x1050 resolution... 

max-possible resolution was 1280x1024!!! 

any solution?

---

### Post by jerrylamos on 2007-03-13
A couple thoughts on max resolution.  

1.  You could try xorg yourself, if you haven't, by doing:
Ctrl-Alt-F1
Killall gdm
sudo dpkg-reconfigure xserver-xorg
This gets a bunch of screens where you can choose driver, video memory, keyboard, ...  In my case, Ubuntu didn't realize the video memory was 65536KB.  I'm not sure what you have.  This is the big limiter on resolution.

About halfway thru xorg will ask if you want to auto detect the monitor.  You could, to see if it will give you 1680x1050, or you could enter the parameters manually.  It'll need to know horizontal and vertical frequency range, resolution, color depth (example 24).   One source of the required data is specs from the manufacturer either what was delivered with the unit, or on-line.  I also fire up XP and look at the Display Settings to see what the data could be.

If this all works, then do
startx
to see if it will go and what you got.

As you might gather I've been thru this a lot with different Ubuntu releases.  I'd rather not have to, especially on every CD Live boot.

On Ubuntu click System, Preferences, Screen resolution to give you the choices it can run.  I don't have Xubuntu up at the moment (this is Dapper) to see the click sequence because I'm rsync'ing today's build.

2. Another possibility is download & try CD Live Simply Mepis which has a Ubuntu base but different hardware detection code, and/or CD Live PCLinuxOS to see if either of them can give you the right resolution.  Another one that works for me is CD Live Puppy Linux, a small distro (90MB) that does give lots of screen resolution choices.  That's a test of what could be done with Linux and I believe they are open source" if Xubuntu wants to step up to the plate.

There's a "summer student" posting of possible student Ubuntu jobs on Wiki where I've suggested they improve Ubuntu graphics/monitor but that would be a while even if they decided to take it on.

So far I clearly prefer the Ubuntu community and hope they will step up to the plate to at least match the competition.

Hmmm....Jerry

---

### Post by obocho on 2007-03-13
first of all, thx : )

but, 1680x1050 resolution works with ubuntu, kubuntu, pclos, fedora 7, etc...
the only problem is with (X)ubuntu : (

I'll try the first way, if it works I'll write back : )))

thx

obocho

---

### Post by jerrylamos on 2007-04-08
As of about 20070402 Xubuntu gets 1280x1024 with LCD monitor and Intel 82845G graphics controller.  Kubuntu picked it up about that time or maybe a day later.  Since Ubuntu's now below 700 mb as of 20070408 I could write a CD and will try it shortly.  I expect it will work because that seems to be common code.

I checked xorg.conf and it now reports correctly the graphics controller and screen type as well as the resolutions.  Give it a go.

Cheers, Jerry :)

---

### Post by jerrylamos on 2007-04-09
Yep, Ubuntu as of 20070408 fits on 700 mb disk.  This configuration 1280x1024 LCD with Intel 82845G controller came up fine.  Before that only 1024x768.  Great going!

Chees, Jerry :)

---

