---
title: "Freeze - but keyboard/mouse still works"
date: 2005-10-11
forum: Desktop Environments
---

### Post by Svenne on 2005-10-11
I've been experiencing some problem with my Hoary-system lately.

The system freezes at random, causing me to make a hard reboot/shutdown. At first I thought the problem was related to cpu-load (heat- or powerproblem) since it regularly froze while gaming (ET), but then the system froze when I only used firefox and OpenOffice.
The funny thing about the problem is that only the screen freezes. I can still use the mouse (if not inside a fullscreen game) and the keyboard. That means I can kill X with ctrl+alt+backspace... BUT, when I get to the tty-prompt I can't log in. I can type my username and press enter (and it shows up ok on the screen), but the system never responds with a password-prompt. It is as if the system is too busy to handle my login-attempt. The problem exists on all tty's.

Unfortunately, I've been doing a lot of reconfiguring of the machine, which means there are lots of possible sources of my problem:

- Graphicscard: I switched from a ATI Radeon 9600XT to a ATI Radeon 9800Pro. Shouldnt make much difference since the driver is the same.
- Memory: I removed my old 512MB RAM stick and replaced it with the 2 new 512MB sticks. I have run Memtest86+ on them, and they give no errors. The reason that i dont use my old stick anymore is that my 3rd memory-port seemed to cause errors. Still... with only the 2 sticks in the system MemTest finds no errors.
- Power: I am only using an old 300W psu, which may not be able to handle the new graphicscard and memory. 
- Ubuntu: I am using Hoary with constant backport-upgrades (from the official backport-repository only).

At first I concidered not to bother you at this forum, since it seemed more likely that it is a hardware-problem (because of all the new hardware), however it doesnt seem like a hardware-freeze since I can still use the keyboard to change session. If the freeze happens while i'm in the gnome-desktop, the mouse curser still moves perfectly with my mouse-movements, but I can't click anything or open any gnome-menus. The screen is frozen (as well as any open applications) but the input-devices are not!

Any help would be appreciated.

---

### Post by Svenne on 2005-10-11
Hmm... it just froze up on me again... 
This time I hadn't used the PC for over an hour. I got back to the pc and chose from my gdesklet-starterbar to start Thunderbird. The starterbar reacted (animated) as usual, but Thunderbird never started. I then clicked on the gnome "application"-menu to start Tbird that way, but I never got that far. The applicationmenu dropped down as usual, but the entries in the list didnt show any icons next to the name... and at that exact second the system froze on me... or rather (like always) the _gui_ froze on me. I can still move the mouse-cursor (but I can't click anywhere) and the keyboard works like it should. And this time, since I hadnt opened any application-windows yet, I noticed that my gdesklet FTB-monitors still runs and shows perfectly. The uptime-counter still runs and the cpu-monitor still plots it's diagram like it should (with no anamoly - still ~2-6% cpu usage). 

I really dont get this. The system seems to run perfectly, but it wont let me interact with it. I can (with the keyboard) switch tty-session but not log in (the password-prompt never shows up after i type my username).

The only desktop-apps I ran at the freeze was Gaim, X-chat and gdesklets. The gaim-icon on the gnome-panel seems to have crashed tho. It doesnt show up next to the gdesklet-icon like it usually is. Can it be gaim that crashes and locks some resources? I am not very linux-experienced thus really fumbling in the dark at this one.

---

### Post by terasurfer on 2005-11-20
I think I have been experiencing a similar problem.  In my case, I have narrowed it down to gaim.  At first I thought it was the guifications plugin, but I have that disabled and still encounter the problem.  

If I look at top, Xorg shows up with 99%-100% constant CPU usage.  If i kill gaim, everything returns to normal.  The problem seems to happen completely at random, but after relatively long intervals (every few days).  Gaim does still respond while this is happening, but any refreshing of the interface takes a VERY long time.

---

