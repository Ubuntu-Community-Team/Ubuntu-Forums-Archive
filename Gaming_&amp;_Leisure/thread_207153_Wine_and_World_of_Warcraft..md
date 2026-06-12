---
title: "Wine and World of Warcraft."
date: 2006-07-01
forum: Gaming &amp; Leisure
---

### Post by ATOMIC2 on 2006-07-01
I'm having problems with both to be honest.
I'll start from the very beginning;

Having used the "How To" guide from the following link, [http://appdb.winehq.org/appview.php?versionId=5109](http://appdb.winehq.org/appview.php?versionId=5109) I have sucessfully downloaded, complied and installed Wine 0.9.16 with it's corresponding World of Warcraft patch without any errors.

However, when I type "winecfg" in the Terminal, I am prompted with the following error message.

```
fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
```

This does not or atleast does not seem to effect anything at this point in time.

My next problem is when I access the, "Drives" tab. I recieve this.

```
err:winecfg:load_drives GetVolumeInformation() for 'D:\' failed, setting serial to 0
```

Again, I don't believe this has any effect on what I am doing.

The next problem however, does. When I click on the, "Audio" tab I recieve this.

```
*** glibc detected *** free(): invalid pointer: 0x7c06bb50 ***
wine: Assertion failed at address 0xffffe410 (thread 0009), starting debugger...
```

Because of this I am unable to set OSS as the default audio instead of ALSA.

My next problem is in the, "Graphics" tab. If I do not emulate a Virtual Desktop, any program which runs full screen, i.e World of Warcraft. My monitor displays an error message stating it cannot show the current display and I am forced to reboot my PC.

These are the problems I have faced in, Wine. Now onto World of Warcraft with Wine 0.9.16.

D3D Works, very very laggy and both the Standard Mouse and the World of Warcraft mouse lay over each other. The mouse is simply annoying, but playable. The lag I recieve in D3D is unbareable however.

As for running WoW in OpenGL, It will either crash while the loading screen is up, or while the loading screen is up and the background downloader pops up or not long after the loading screen disapears and I am set to play.

I haven't found answers to any of these problems searching the forums so any help/ideas would be greatfull.

I have the latest ATI Linux drivers installed and the following is my PC Specs.
Ubuntu 6.06 x86, AMD 3500+ Athlon 64, Asus A8VE-Deluxe, Powercolor ATI Radeon X800 GT, Sound Blaster Audigy 2, 1GB Giel RAM, Seagate 120GB HDD SATA-IDE.

---

### Post by Klemik on 2006-07-01
Try to use cedega instead of wine. Cedega is made for playing games, wine (imo) is made for launching small apps.

---

