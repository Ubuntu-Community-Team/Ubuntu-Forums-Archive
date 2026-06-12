---
title: "SuperTuxKart problem (0.7.1-b)"
date: 2011-05-06
forum: Gaming &amp; Leisure
---

### Post by 3602 on 2011-05-06
Well I added the PlayDeb and downloaded (installed) STK from there.
Problem: On some tracks, when the race starts there is immediately a "penalty time" warning even if I haven't pressed on anything. When the Go disappears, I cannot move. Cannot advance, cannot go back; although I see the wheels veer when I steer.
On some other tracks, there is no such warning and I can actually advance, but the gameplay stutters like 3-4 rapid screen "pulsings" per one second.
I tried remapping the keys and decreasing the video quality. Doesn't help.

Please help! Thank you very much!

EDIT: Plain old 0.7 works like a charm. So it's a version fault?

---

### Post by Arthur_D on 2011-05-06
Hi, do you have any gamepads connected? If so please start STK with
```
supertuxkart --gamepad-visualisation
```and post the output here. (If it's massive, please just take a snippet of 10 lines or so instead of dumping it all here).
And even if you don't have any actual gamepads connected, something might act like it, so you could try running with this flag anyway.

Regarding stuttering gameplay, could you perhaps try the [static binary]("http://supertuxkart.sourceforge.net/Downloads#header_linux") instead. If Irrlicht hasn't been built in release mode for the version you're using, performance will be severely affected. Otherwise, check video drivers etc.

---

### Post by 3602 on 2011-05-06
Although I have no gamepads installed, there is an "Accelerometer" entry under the Devices list and I had it disabled.
When I try to run your command the computer screen converts into a black background with white grids on it, and starts to flash rapidly. Nothing responds although I can see some output on the terminal. I tried Crtl-C, Ctrl-D and Ctrl-X and none of them killed the process. The only way to get out was Ctrl-Atl-F1 and sudo reboot.
I did try the static bin. No stuttering but the Penalty Time is still there.
So why is the old 0.7, downloaded from SourceForge, working?

---

### Post by Arthur_D on 2011-05-06
Could you please try to report this on the official [SuperTuxKart forum]("http://supertuxkart.net/forum")? There you'll probably get better help than I'm able to give you. And while you're at it, include the output from
```
supertuxkart --gamepad-debug
```into your bug report (different command from the first one; it should hopefully not lock things up for you).

---

### Post by 3602 on 2011-05-06
Thanks for the address. Now I'll have to figure out how to actually post!
Will try to run that command. I'll edit with results.

EDIT: Got into the game but also flashy all the way. I was able to click the Quit icon and get out.
The output is really long and I cannot see the top portion. How to see that? Thank you.

EDIT II: Rapidly pressed ESC before the really long gamepad motion output. Great now I have a Segmentation Fault.

---

### Post by Arthur_D on 2011-05-07
What you can do is use
```
supertuxkart --gamepad-debug > ~/gamepad-debug.txt
```
This will pipe the output to a text file in your home folder. On the STK forums, you can then upload it as an attachment. You needn't run this for long, since the ouput would be really huge otherwise.

Thanks for the patience. :)

---

### Post by rudysuryanto on 2012-02-02
I have the same problem, while play supertuxkart, my video card driver is SIS

root@rudy-P4M800PRO-M:/media/Videos_1TB/Software/supertuxkart# supertuxkart --gamepad-debug
Irrlicht Engine version 1.7.2
Linux 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:50:54 UTC 2012 i686
[FileManager] Data files will be fetched from: '/usr/share/games/supertuxkart/'
[IrrDriver] Creating NULL device
Irrlicht Engine version 1.7.2
Linux 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:50:54 UTC 2012 i686
[IrrDriver] Trying OpenGL rendering.
[IrrDriver] Tring to create device with 32 bits
AL lib: pulseaudio.c:331: PulseAudio returned minreq > tlength/2; expect break up
startMusic : m_normal_filename=</usr/share/games/supertuxkart//data//music/MayDayMayhem.ogg>, gain=0.7
WARNING: Music not playing when it should be. Source state: 4116
Segmentation fault

how to fix it thanks?

---

### Post by Arthur_D on 2012-02-02
Please try to use the latest version of SuperTuxKart, which at the time of writing is 0.7.3. If you still get the same problem, I have a feeling that you don't have 3D acceleration for your driver, and you should use the "Additional Drivers" utility to install any missing graphics drivers, reboot and try again.

---

### Post by Arthur_D on 2012-02-02
Sorry, double post.

---

### Post by rudysuryanto on 2012-02-02
sorry, exactly my video card is  VIA P4M800PRO

---

### Post by Arthur_D on 2012-02-03
Did you enable any proprietary graphics drivers in "Additional Drivers"? I think that may solve your problem.

---

