---
title: "[SOLVED] Ati Driver Splash Screen Problem Kubuntu 8.10"
date: 2008-12-29
forum: General Help
---

### Post by BreeZier on 2008-12-29
PROBLEM SOLVED -- SEE 2ND POST

Hay, I'm new around here :)

I have been searching for a solution to my problem on these forums, couldn't find :/

So here i go :P

I managed ton tri-boot ubuntu on my hdd. I managed to install KDE with success, trying stuff, and Installed CCSM compiz fusion -- tried to make it work in my new Kubuntu, couldn't. So I logged out and came back in a Gnome interface, this time enabling CCSM was simple.

I have Ati Drivers installed for my radeon hd 4850, everything was working fine. Note that i had the same problem before installing CSSM, after getting the updates, at that time i simply reinstalled.

What happened is that after enabling CCSM in Gnome and pretty much every visual effect, playing around (everything working just fine) -- meanwhile installing latest updates (around 200mb) -- I rebooted to see the Kubuntu loading, then the screen switches resolution to get to the Kubuntu login, but oops no login screen, only a black screen with 5 Kubuntu splash screens in the top side by side...

how pretty.

I know about the ctrl-alt-f1 command, which works. But my knowledge stops pretty much -- there.

So - I guess the problem comes from either the Updates or the CCSM, or the ATi Drivers. Note that when i first had that problem, CCSM wasn't installed... so Ati or Updates...

Anything i can try without reinstalling everything... :/

Thank you!

---

### Post by BreeZier on 2008-12-29
Problem Solved -- Thank You

45 mins later, after some intensive reading i came across this site:

[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

which made me try some commands in control-alt-f1 mode

sudo dpkg-reconfigure xserver-xorg
then
control-alt-f7
then
control-alt-backspace

that gave me a white screen with a mouse on it.
I rebooted, Kubuntu login screen appeared, logged in Gnome

tried to restart ccsm, couldnt use enhanced effects in system -> preference --> appearance

So, using a gksudo launcher and my "execute enabled" ati driver downloaded .run file, i reinstalled Ati Driver,

Went in the terminal, typed
aticonfig --initial -f

reboot

everything works just fine now

wow...

and i tought i knew a lot in comps...
i guess i know a lot in windows eheh...

That cube effect is F nice :P

now time to get some more desktop customization ;)

---

