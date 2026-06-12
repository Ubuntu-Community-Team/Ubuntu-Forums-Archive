---
title: "Need help getting Stepmania to work x.x"
date: 2007-06-22
forum: Gaming &amp; Leisure
---

### Post by mattmagician on 2007-06-22
So okay, i just downloaded the stepmania for linux, and followed the instructions. i have the folder on my desktop, and when i double click the start application, i can't. am i doing something wrong or?
thanks.
Matt

---

### Post by Motoxrdude on 2007-06-22
WHat do you mean you can't? Does it give an error? Can you link the instructions here?
EDIT: I am currently going to try and install stepmania. If it works for me i will post a howto.

---

### Post by mattmagician on 2007-06-22
ok, thanks! it doesnt come up with an error, it just shows the tiny little thing you see when most things start up, then never does anything.

---

### Post by Motoxrdude on 2007-06-22
It gives me some sound driver error. Download the windows version and run it in wine.
To install wine go to your terminal and type
```
sudo apt-get install wine
```
then download the windows version of stepmania and right click, select "Open with other application>>Use custom command and type wine. Press ok and it **should** work.

---

### Post by Cappy on 2007-06-22
Or, to run the linux version you need to run stepmania in a terminal so you can see the error it gives you.
If you get an error post all you can back to this thread.

you'll have to change to the StepMania directory and then
```
./stepmania
```

P.S. Post the directory you extracted it in, if nothing else

---

### Post by mattmagician on 2007-06-22
ok, i got:
matt@matt-ubuntu:~$ /home/matt/StepMania-3.9/stepmania
StepMania 3.9
Log starting 2007-06-22 21:53:03
Loading window: gtk
OS: Linux ver 020615
Crash backtrace component: x86 custom backtrace
Crash lookup component: dladdr
Crash demangle component: cxa_demangle
Runtime library: glibc 2.3.6
Threads library: NPTL 2.3.6
TLS is available
ALSA: Advanced Linux Sound Architecture Driver Version 1.0.10rc3 (Mon Nov 07 13:30:21 2005 UTC).
ALSA Driver: 0: SBLive! Value [SB0101] [Live], device 0: emu10k1 [ADC Capture/Standard PCM Playback], 31/32 subdevices avail
ALSA Driver: 0: SBLive! Value [SB0101] [Live], device 2: emu10k1 efx [Multichannel Capture/PT Playback], 8/8 subdevices avail
ALSA Driver: 0: SBLive! Value [SB0101] [Live], device 3: emu10k1 [Multichannel Playback], 1/1 subdevices avail
ALSA Driver: 1: VIA 82C686A/B rev20 [rev20], device 0: VIA 82C686A/B rev20 [VIA 82C686A/B rev20], 1/1 subdevices avail
ALSA: dsnd_pcm_hw_params: Cannot allocate memory
ALSA: Got 20 hardware buffers
Sound driver: ALSA
Video renderers: 'opengl'
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
ptrace failed: Operation not permitted
ptrace failed: Operation not permitted

StepMania has crashed.  Debug information has been output to

    /tmp/crashinfo.txt

Please report a bug at:

    [http://sourceforge.net/tracker/?func=add&group_id=37892&atid=421366](http://sourceforge.net/tracker/?func=add&group_id=37892&atid=421366)

*** glibc detected *** corrupted double-linked list: 0xb7bab358 ***
Fatal signal (Aborted) while still in the crash handler

---

### Post by Motoxrdude on 2007-06-22
Do what i said in my last post, see if it works.

---

### Post by Cappy on 2007-06-22
> Xlib: extension "GLX" missing on display ":0.0".

Do you have your video drivers installed? Are you running Dapper?
Turn off Beryl before you launch the game also.

---

### Post by mattmagician on 2007-06-22
Beryl isnt in use, video drivers are installed, and i am running dapper.

---

### Post by Cappy on 2007-06-23
Check
```
gksudo gedit /etc/X11/xorg.conf
```
and make sure that under
Section "Module"
you have a
```
Load           "glx"
```
and a 
```
Load           "dri"
```

If that doesn't work, the only option I know of is to reinstall your video card drivers.

```
*** glibc detected *** corrupted double-linked list: 0xb7bab358 ***
```
Since the video card error came first, I'm guessing the program crashed due to that, and then it caused the error above came from the program not handling the missing glx module.

---

### Post by mattmagician on 2007-06-23
how do i reinstall my video card drivers?

---

### Post by Cappy on 2007-06-23
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-c3f28515df1775ec5e62e78fd6c0f8f54e5f9302](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-c3f28515df1775ec5e62e78fd6c0f8f54e5f9302)

---

### Post by natachinha on 2007-07-12
Hi, I have a similar problem and tried to run stepmania with Wine. It worked, but I have a question: where can I find the program's folder? To add my songs, and everything else... 
I'm sorry if it's a dumb question, but I'm a begginer ubuntu user. Thanks for the help!

---

### Post by Cappy on 2007-07-19
> **natachinha said:**
> Hi, I have a similar problem and tried to run stepmania with Wine. It worked, but I have a question: where can I find the program's folder? To add my songs, and everything else... 
I'm sorry if it's a dumb question, but I'm a begginer ubuntu user. Thanks for the help!

Stepmania will be in your .wine folder

---

