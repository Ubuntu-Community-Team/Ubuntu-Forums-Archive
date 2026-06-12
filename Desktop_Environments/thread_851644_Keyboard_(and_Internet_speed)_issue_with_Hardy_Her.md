---
title: "Keyboard (and Internet speed) issue with Hardy Heron"
date: 2008-07-06
forum: Desktop Environments
---

### Post by kovenant on 2008-07-06
hi.  im new to linux and currently am running dual boot config with Vista & Ubuntu (hardy heron). let me give the specs for my rig:

eVGA 680i SLI (A1) w/ bios P25
Vista Premium 32-bit / Ubuntu 8.04 Hardy Heron
Intel C2D E6600 @ 3.38ghz
2GB G.SKILL DDR2 800 RAM @ 4-4-3-5 1t
eVGA GeForce 8800GTS 320MB @ 600gpu 900mem
2x Seagate Barracuda 320GB 7200 RPM
LG 18X DVD±R DVD burner
Razor Copperhead mouse
Microsoft Reclusa keyboard
Thermaltake Soprano DX Black ATX Mid Tower
OCZ GameXStream ATX12V 700W PSU
SAMSUNG 206BW Black 20" 2 ms Widescreen LCD


alright - i am experiencing 2 problems (only) while running Ubuntu.  the 1st and most annoying is that my spacebar sticks (or repeats.)  the first instance it is noticeable is during login screen.  when prompted for username: the spacebar begins repeating on its own and you have to backspace to the beginning of the line to type in your username.  even now as i am typing this thread, if i pause after pressing the spacebar, i get hit with a long line of repeating spaces - until a press a different key.  is there a fix or driver that will eliminate this problem?

2nd - my internet connection while using Ubuntu is drastically slowed down.  while taking a speed test online shows a slightly faster connection when running under Ubuntu, the simple fact is that getting a webpage to load takes alot longer on Ubuntu (i use firefox 3 on both my Vista and Ubuntu OS's.)  any idea what could be causing this?  maybe a linux specific driver for my network card?

id love to hear if anyone else is experiencing these problems and/or if there are somethings i can try to eliminate them.  thanks!

---

### Post by pytheas22 on 2008-07-06
For the keyboard: I'm not positive that it will help, but if you go to Preferences>Keyboard, you can experiment with different settings.  Changing keyboard model under the Layouts tab from something other than "generic" might be especially helpful--you can choose a Microsoft keyboard specifically.  You can also change key repeat times and sensitivities, which might help at least to make the problem less dramatic.

As for the Internet: if your speed tests don't indicate a problem, then I'd blame Firefox rather than the Internet connection.  Have you tried using an alternate browser, like Konqueror or Opera, or even the Windows version of Firefox or Internet Explorer?  Are you able to download files from servers at the same speed as you can in Windows?

---

### Post by kovenant on 2008-07-07
hi pytheas22 ~ i had already set Keyboard layout to Microsoft, but i played around with the "key repeat" delays a bit... nothing changed.  when i UNchecked key delay, it fixed the problem with repeating.  the only thing it doesnt fix is when Ubuntu loads, the username still gets hit with a repeating spacebar... im wondering if there is something in my BIOS that tells the computer to start the keyboard with a Spacebar key - weird, but ill probably go look in there when i get some time.  at least i can type without that irritating spacing.  cant hold down backspace or arrow keys though-  since key repeating is turned off.

as for internet - read on these forums to go here:
[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html]("http://www.ubuntugeek.com/speed-up-firefox-web-browser.html")

which did seem to speed things up in FF... also saw about FasterFox, but they dont have a version that currently works with 3.0


anyone else have ideas on the spacebar keyboard problem?  id rather have Key Repeating enabled if there is a fix :)

thnx!

---

