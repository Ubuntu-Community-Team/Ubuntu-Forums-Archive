---
title: "pSX trouble"
date: 2008-07-07
forum: Gaming &amp; Leisure
---

### Post by andyhowington on 2008-07-07
Well I finally gave up on PCSX because I couldn't get it to read my .iso files.

Now onto pSX. I installed it according to [_[COLOR="Blue"]this guide[/COLOR]_]("http://www.ubuntugeek.com/install-psx-emulator-on-ubuntu-amd64.html"), and it did not work until I found some old advise in these forums and ran ```
sudo apt-get install libgtkglext1-dev
``` (thank you FranMichael)

I have the BIOS file, and have put it into the directory /home/myusername/pSX/bios. However, when I run ./pSX i get the following message: "**BIOS not found** - This emulator requires a BIOS image which must be installed in the bios folder," Cancel/OK.

I hit OK and select the BIOS which I put in the folder and hit OK, and it closes. In terminal I see:```
pSX: pcm_params.c:2259: snd_pcm_hw_refine: Assertion `pcm && params' failed.
Aborted
```When I open it again I get the same thing.

Any suggestions? Or, alternatively, could someone give me in depth instuctions on how to configure the PCSX CD-ROM to run a .iso file? Do I need to "mount"? I have Gmount. Tinkering in PCSX I got a few results: 
1. black screen
2. White Sony screen, then it just stays there
3. A "Main Menu" where the options were Play CD and Memcard I think. Something like that. But play cd was like for music and there was nothing there. memcard was empty.

Thank you I really appreciate your help!:popcorn:

---

### Post by acoustibop on 2008-07-08
Sounds like you have a soundcard problem, andyhowington - you need to tell us more about your machine specs and Ubuntu (?) version.

---

