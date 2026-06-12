---
title: "Wine 1.2.2 and Homeworld 2 crashing"
date: 2011-02-15
forum: Gaming &amp; Leisure
---

### Post by zyrex on 2011-02-15
Hi,

Ok im pretty new to wine.  I have installed a fresh install of wine, and winetricks.  Notepad runs smoothly no hiccups.

I then installed steam works hundreds and so does CS-source, but when running Homeworld 2 i constantly get the following:

fixme:ntoskrnl:KeInitializeMutex stub: 0x1112d0, 1
fixme:ntoskrnl:KeInitializeMutex stub: 0x1112f0, 1
fixme:ntoskrnl:KeInitializeEvent stub: 0x111320 1 0
fixme:win:EnumDisplayDevicesW ((null),0,0x32f0b0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e934,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e9e4,0x00000000), stub!
fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
fixme:devenum: DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum: DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found

tried running with the -nopbuffer and noVDM and video errors switch... nothing still crashes after a black screen.  Tried to run it with -opengl  same problem. Its also set to run in an emulated window of 1152x860.

can someone help me here as to where i can fix this and get it running?

---

### Post by searchfgold6789 on 2011-02-15
I would go ahead and post that on the [Wine Section of the ubuntuforums]("http://ubuntuforums.org/forumdisplay.php?f=313") instead :)
Looks like the Mod hasn't moved it yet...

---

### Post by Perfect Storm on 2011-02-15
Wine related, thread closed.

---

