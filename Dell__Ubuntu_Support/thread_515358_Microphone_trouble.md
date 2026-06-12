---
title: "Microphone trouble"
date: 2007-08-01
forum: Dell  Ubuntu Support
---

### Post by kuja on 2007-08-01
So I just got my shiny new 1420n from dell right. Day 1 and it's on to exploring as well as settinng up Kubuntu. I decided to set up skype since it's the first time I've had a microphone port to play with in a while. I played with a mess of settings and I just can't get the mic to work right. Anybody else having any trouble?

---

### Post by AndrewTheArt on 2007-08-01
My guess is that your mic isn't turned up in the audio settings. Right click on the KMix icon at the bottom right of the screen, select "Show Mixer Window", go to the Input tab, and pull up the mic channel a bit. If you don't have the KMix icon run kmix from a terminal. I had this problem and this was definitely the solution.

---

### Post by daahli on 2007-08-01
I had the same problem too. For some reason Ubuntu defaulted to a muted capture setting. If you unmute the capture setting in the mixer the mic should work.

By the way, does the 1420n have a built in mic?

---

### Post by kuja on 2007-08-01
It doesn't have a  whole lot of settings to play with. Under input I have "Capture" switched on and turned up to 75%. Under Switches I have "Input Source" set to "Mic"(I also tried setting it to "Front Mic". That's pretty much all that's there for me to play with as far as I can see. And well, I'm getting nothing :(

---

### Post by kuja on 2007-08-01
> **daahli said:**
> By the way, does the 1420n have a built in mic?
Nope.

---

### Post by daahli on 2007-08-01
There is a capture and a capture1 setting. Try capture1, maybe that will help.

---

### Post by kuja on 2007-08-01
No. See attached screenshots.

---

### Post by AndrewTheArt on 2007-08-03
That's odd - I have a LOT more options that just "capture". Possibly, Ubuntu didn't recognize your sound card correctly, and it's using some generic driver in place of a more specific one. (Is HDA Intel generic?) Beyond this, I can't really offer any help.

---

### Post by kuja on 2007-08-04
```
blackwaltz@dell:~$ lscpi -vv
.... 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
        Subsystem: Dell Unknown device 01f3
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 21
        Region 0: Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000
        Capabilities: [70] Express Unknown type IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s unlimited, L1 unlimited
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed unknown, Width x0, ASPM unknown, Port 0
                Link: Latency L0s <64ns, L1 <1us
                Link: ASPM Disabled CommClk- ExtSynch-
                Link: Speed unknown, Width x0
....
```

```
blackwaltz@dell:~$ lsmod | grep snd
snd_hda_intel          22680  1
snd_hda_codec         240908  2 hsfhda,snd_hda_intel
snd_pcm_oss            44544  0
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
snd_seq_midi            9600  0
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm

```

---

### Post by Denny Johnson on 2007-08-05
> **daahli said:**
> 
By the way, does the 1420n have a built in mic?
The webcam option on the 1420 includes a mic.
Seems that it's not even an option on the n version.

---

### Post by ugm6hr on 2007-08-05
I had a similar problem - albeit on a totally different laptop.

But it wouldn't hurt to have a look at the Terminal settings, in case KMix is misbehaving...

[http://ubuntuforums.org/showthread.php?t=506515](http://ubuntuforums.org/showthread.php?t=506515)

---

### Post by ajohns315 on 2007-08-09
IS IT POSSIBLE THAT THE SETTINGS NEEDED HAVE NOT BEEN ACTIVATED? IE. ,THE PREFERENCES OPTION IN THE 'EDIT' MENU. 

I WAS UNABLE TO GET MY HEADPHONES TO WORK AND THEN REALIZED THAT i HAD TO CHECK THE CAPTURE BOX IN THE PREFERENCES WINDOW.

---

### Post by kuja on 2007-09-05
I should have replied to this thread much, much sooner, but I guess it slipped my mind. 
> **ugm6hr said:**
> I had a similar problem - albeit on a totally different laptop.

But it wouldn't hurt to have a look at the Terminal settings, in case KMix is misbehaving...

[http://ubuntuforums.org/showthread.php?t=506515](http://ubuntuforums.org/showthread.php?t=506515)

This looked really promising, (in fact, IIRC kmix really was misbehaving), but after amping up the capture volume in amixer I'm still getting nothing. I'm going to try this with a different mic just to see if this mic hasn't gone bad or something.

---

### Post by Flavian on 2007-09-07
Did you find anything that solved your problem!
I've got the EXACT SAME Problem on two laptops, (my brother's and mine)
It's an ASUS and Fujitsu-Siemens Laptop... :(

---

### Post by Afishionado on 2007-09-07
Dell Inspiron 1420n; I'm still running the Ubuntu install the machine came with (no KDE). I had to fiddle a bit myself to get it working; the Gnome sound control applet seems to have had some vital bits amputated in the last upgrade. :(

I had to run alsamixer from the command line to get things working. Once it's running, use the left and right arrow keys to go through the options in a screen, up and down arrows to change the current option, and tab to move from one screen to the next.

Important bits: The rightmost option in the first screen **must** be set to "Mic", or an external microphone won't work at all. Then, go to the second screen and change the capture volume there; out of the box, it's set ridiculously low.

I've attached screenshots of my settings below; the capture volume is probably cranked too high, but at least this way you'll know whether or not it works. :)

As usual, I recommend using Audacity to make sure that the microphone is working. Once you can record and play back yourself babbling in Audacity, fire up Skype and use their test call service.

:guitar: <-- for you to test your mike with ;)

---

### Post by Flavian on 2007-09-09
Hi.
Thanks for your kind way of helping me ;) here for you, to say thank you ---> :popcorn: 

Even though I have a problem, my settings in alsamixer look slightly different then yours :( and I can not record anything :(
I'll just post how they look.
I hope you can help me! Not being able to use the microphone is REALLY annoying :(

Btw: Is there a way to get the INTERNAL Microphone to work as well?
Thanks in advance
Flo

---

### Post by ugm6hr on 2007-09-10
> **Flavian said:**
> Hi.
Thanks for your kind way of helping me ;) here for you, to say thank you ---> :popcorn: 

Flo

Looking at your alsamixer - you have "mic" muted - and there is no volume for "Front Mic".

Try unmuting "Mic" (press "M"), and also press Tab in alsamixer and have a look at the "Capture" settings.

If that doesn't reveal anything, have a look at the output from:
```
amixer
```

My link in my previous post might give you some ideas.

---

### Post by Denny Johnson on 2007-09-12
Thanks for all the suggestions, especially Afishionado. Worked for me.
I'm a newbee, just got a 1420n, using the command line is getting easier w this very clear instruction w attachments.
Very happy to have the mic working now.

---

### Post by Denny Johnson on 2007-09-16
mmmmmm........I've lost the mic again, the alsa mixer settings remain stable, but the KMIX do not.
If I Shut Down or quit KMIX while running, when I reopen KMIX I get the following: 

denjohn@dell:~$ kmix
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
denjohn@dell:~$ 

and the slider will be down to zero on the input tab 

I'm a newb, any suggestions appreciated.

---

### Post by brianves on 2007-09-16
hey there sounds like your DCOP server isn't working right,  this won't help your mic,  but there are a lot of programs that won't work with DCOP not up.  
go to terminal
so first  make a copy of /etc/X11/xorg.conf
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
now edit xorg
sudo nano /etc/X11/xorg.conf
scroll down till you see 
#Section "InputDevice"
#       Driver          "wacom"
#       Identifier      "stylus"
#       Option          "Device"        "/dev/input/wacom"
#       Option          "Type"          "stylus"
#       Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#       Driver          "wacom"
#       Identifier      "eraser"
#       Option          "Device"        "/dev/input/wacom"
#       Option          "Type"          "eraser"
#       Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
#EndSection


#Section "InputDevice"
#       Driver          "wacom"
#       Identifier      "cursor"
#       Option          "Device"        "/dev/input/wacom"
#       Option          "Type"          "cursor"
#       Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
#EndSection

and further down

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection


now did you notice the # signs in front,  well you shouldn't have those.  But chances are that's your problem with DCOP.  put those number signs as I did. they omit whatever's after them.   then save.... ctrl+X,  it should ask if you want to save hit Y.  then it should ask the path...  Enter.  
ok.  restart your computer,  if all goes well your DCOP shouldn't give you any problems.  if your computer doesn't boot back up,  which happened to me the first time I did this  (I forgot the last 3 # signs)  just go to the prompt and do sudo nano /etc/X11/xorg.conf.backup  
change everything back the way it was then save it to
/etc/X11/xorg.conf
and restart,  but if you have those wacom devices in there,  chances are they are the culprit.  good luck.

---

### Post by Denny Johnson on 2007-09-17
brianves
Thanks for that, but I'm gonna have to get a bit more comfortable w my new system before I take that on. That, a real clear mind and a chunk of time to absord what I'm doing.
The mic is working, tho I have to reset Kmix and alsamixer [sometimes] if I shut down.
Kmix opens even if I get all that in the terminal that I posted previously.
I'll post results when I give your suggestions a go.
Thanks

---

### Post by Brandon.Viking on 2007-09-17
I also was having great difficulty in selecting the correct input for the mic to work. I had to go through the mixer settings until I added just about every option possilbe. I found that I had turned enough on to get it working now but I didnt check which option I turned on and tweeked. 
Keep playing with the mixer might be the thing.

---

### Post by Denny Johnson on 2007-09-21
Recap:
After changing Kmix settings suggested by kuja on pg 1, and alsamixer settings suggested by afishionado on pg 2....the headset mic worked..... but I'd lose the Kmix input setting whenever I shut down.
Strange as this seems, the fix seemed to happen in the SETTINGS tab in CONFIGURE KMIX, I changed the SLIDER ORIENTATION from HORIZONTAL to VERTICAL .
The default setting was HORIZONTAL, tho the sliders appeared vertical.
When I changed the ORIENTATION setting to VERTICAL, the sliders appear horizontally, but the input volume is not lost when rebooting.

---

### Post by Denny Johnson on 2007-09-21
> **Denny Johnson said:**
> Recap:
After changing Kmix settings suggested by kuja on pg 1, and alsamixer settings suggested by afishionado on pg 2....the headset mic worked..... but I'd lose the Kmix input setting whenever I shut down.
Strange as this seems, the fix seemed to happen in the SETTINGS tab in CONFIGURE KMIX, I changed the SLIDER ORIENTATION from HORIZONTAL to VERTICAL .
The default setting was HORIZONTAL, tho the sliders appeared vertical.
When I changed the ORIENTATION setting to VERTICAL, the sliders appear horizontally, but the input volume is not lost when rebooting.
I've recently posted the above, and it worked, but I've come to see things differently:
[qualifier] I'm new to this, but it seems that Kmix is a KDE thing, unecessary on a 1420n, should be avoided, and the cause of my DCOP issues.
Perhaps alsamixer settings need to be tweaked, but the main corrections can be readily made by double clicking the [upper righthand corner] speaker icon/EDIT/PREFERENCES [ajohns315 mentioned this in post# 12, but didn't specify how to get there].
Mine are now set PCM, Capture, and Input Source. It seems to be working fine, tho time may dictate a bit more tweaking.

---

