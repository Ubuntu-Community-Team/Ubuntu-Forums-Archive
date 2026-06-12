---
title: "Best Gameboy Advance emulator"
date: 2010-01-19
forum: Gaming &amp; Leisure
---

### Post by blazemore on 2010-01-19
Hello people,

I've used Visualboy Advance before on Windows, and I'd like to play my Gamebody Advance games on Linux.

I installed a version of visualboy advance from the repos (I'm on Karmic, well, Mint 8 ), but can't seem to get it to work.

Can someone help me get up and running with a gameboy advance emulator (preferably VBA since my saves are in this format!) with a GUI, which supports gamepad input?

Or is running VisualBoy-Advance-M through Wine the way to go?

---

### Post by Nevon on 2010-01-19
A while back, I wrote an article on emulating pretty much every Nintendo, SEGA and Playstation consoles (except the latest generation) in Linux. It might be helpful to you.

[http://www.blastfromthepast.se/blabbermouth/2009/04/console-emulation-in-linux-part-1-nintendo-family/#GB](http://www.blastfromthepast.se/blabbermouth/2009/04/console-emulation-in-linux-part-1-nintendo-family/#GB) (link leads directly to the Gameboy section)

I found the best emulator to be visualboy-advance with the visualboy-advance-gtk frontend - the same one you can find in the repos. 

You could also try VBA-M, which is available in native form, so no need for wine. The latest revision I could find was 1.8.0 SVN 877. Here's a link to the .deb file: [http://sourceforge.net/projects/vbam/files/gvbam%201.8.0%20SVN%20877/visualboyadvance-m_1.8.0.877-1_i386.deb/download](http://sourceforge.net/projects/vbam/files/gvbam%201.8.0%20SVN%20877/visualboyadvance-m_1.8.0.877-1_i386.deb/download)

---

### Post by Dayofswords on 2010-01-19
is it weird that i still have a gameboy advance(SP to be exact)

i even have a gameboy pocket and color =\

---

### Post by blazemore on 2010-01-19
Thanks for that vba-m deb link, I'm checking it out now.

---

### Post by AllRadioisDead on 2010-01-19
Visualboy advance works fine for me.

---

### Post by blazemore on 2010-01-19
OK I tried visualboy advance but it doesn't open my save files from VBA-M on Windows.
VBA-M on Linux doesn't have a GUI so I'm going to try it in Wine.

---

### Post by AllRadioisDead on 2010-01-19
Good luck.

---

### Post by blazemore on 2010-01-19
Okay it works but no sound, any ideas?

---

### Post by 5nak3 on 2010-01-19
Make sure Wine is using the same sound system as your system i.e. pulse, oss or alsa?

I have no idea about emulators but this is something that did come to mind right away after reading the thread.

---

### Post by Nevon on 2010-01-20
> **blazemore said:**
> VBA-M on Linux doesn't have a GUI so I'm going to try it in Wine.

Actually, I think there are multiple gui frontends on Linux. Here are instructions: [http://ubuntuforums.org/showthread.php?t=1264130](http://ubuntuforums.org/showthread.php?t=1264130)

---

