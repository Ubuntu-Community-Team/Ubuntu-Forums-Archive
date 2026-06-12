---
title: "Beryl Freezes with Fglrx and XGL"
date: 2007-04-28
forum: Desktop Effects &amp; Customization
---

### Post by aldrlandon on 2007-04-28
Hi, so I just recently installed Ubuntu feisty and followed this guide to install beryl: [Link]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL") 
I already had installed fglrx and set it up according to the ubuntu wiki. My problem is that sometimes after 10 minutes or more, and sometimes after 2 minutes beryl will freeze and I will have to restart the window manager by hitting ctrl-alt-backspace. Its usually when I am resizing a window or am opening a full screen window. I have emerald themes running also which seems to be working fine. Also, if I stay logged on with Beryl running for a long time, my system will become reallllly slow when I come back to use it (especially 3d effects wise). It is absolutely fine after I restart the window manager, though. the command > fglrxinfo gives me this:
> landon@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300/X1550 Series
OpenGL version string: 2.0.6334 (8.34.8)

My system specs are:
-Core 2 Duo E6300 @ 3.1Ghz (32 Degrees Celsius)
-1GB Kingston DDR2 @ 667Mhz
-Ati Radeon X1300 Pro 256MB
-Gigabyte DS3 Rev. 2.0 Mobo
-Ubuntu Feisty Fawn 7.04 64 bit with 32 bit libs

Thanks for any help you may have!

---

### Post by aldrlandon on 2007-04-29
Any ideas?

---

### Post by aldrlandon on 2007-04-29
Please, anyone have the slightest idea?

---

### Post by Neuralgia on 2007-04-29
I also have an x1300 on my inspiron 6400.

I've tried everything, but nothing seems to work. I just get the white screen, can move my cursor, turn the cube, BUT, I just see WHITE everywhere.

The worse part, is that with the same card, in Edgy Eft, everything worked 100%.

:(

---

### Post by aldrlandon on 2007-04-29
Well, I got mine to work by having it be set to copy for the rendering path, but it just freezes all of the time. Anyone else got an idea?

---

### Post by jbernardo on 2007-04-30
I'm having hard freezes with xgl/fglrx on my laptop (ati radeon xpress 200M). I don't even need to start beryl (which gives me a white screen), sometimes xgl freezes by itself.
Any ideas?

---

### Post by aldrlandon on 2007-04-30
To fix the white screen you just start beryl with the commands:
> beryl-manager --no-force-window-manager and
> beryl-xgl --use-copy
to fix the white screen problem, but I still haven't figured out why it slows down and freezes.

---

### Post by jbernardo on 2007-05-01
Thanks, but until I can fix xgl, there's no use in running beryl.
I've now tried to boot with "lapic", "nolapic noapic", etc. as kernel parameters to see if that would help,as the 200m chipset also has some apic problems, but no luck. I still get the freezes in xgl,even without running beryl. As such, it is unusable right now, as when it freezes even alt-sysreq won't work.

---

### Post by spacetree on 2007-05-06
i have a similar problem on edgy. my card is a x200 (express 1100) and it runs fine most of the time. the problem is that sometimes, all of a sudden, it freezes, a mean freeze, i cant even move the cursor, nor the keyboard reacts. I have fglrx, xgl and beryl. The bad thing about this is that after a reboot, the system is unstable and when trying to activate beryl, it freezes again. After some reboots it all comes back to normal, i dont get what is wrong, please someone tell me what happens

---

### Post by lund3n on 2007-08-11
Hi I have the same problem. Thought I solved it :D but apparently this fix doesn't work for all applications ex. Firefox :(
But worth doing it while waiting for a real fix.

(I have Swedish language on my system so don't know the menu names :S)
1. In Beryl Manager click the second menu at the very top (Window manager?)
2. In the left menu click the last button, on the bottom (Resize windows?)
3. Click the middle tab (Behavior?)
4. In the popdown meny chose the third option (Outline)

The problem is that not all applications (Firefox is the only one I know so far) support the outline mode.

---

### Post by rodpck on 2007-08-18
hi,

i'm having the same problem, using an ati 200m series and athlon amd64. the only thing that i found stoped my computer from freezing was changing the window manager to compiz or metalcity, which really sucks since you don't get the 3d effects, i'll keep looking for a way to stop this problem, maybe reinstalling beryl?

---

