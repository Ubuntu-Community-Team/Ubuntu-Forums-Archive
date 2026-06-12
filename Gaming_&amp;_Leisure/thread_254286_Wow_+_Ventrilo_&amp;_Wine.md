---
title: "Wow + Ventrilo &amp; Wine"
date: 2006-09-09
forum: Gaming &amp; Leisure
---

### Post by NickRich on 2006-09-09
Setup 1: OSS Driver selected for Wow & Ventrilo : WoW runs w/ sound.  Ventrilo opens with no sound.  Close WoW and I have sound in Ventrillo.

Setup 2: OSS Driver selected for Vent & anything else(Alsa, ESD or NAS)for WoW: WoW runs w/o sound.  Sound works in Ventrilo.

Any help would be greatly appreciated, as this is the last thing keeping me from completely removing windows.

---

### Post by Watercarver on 2006-09-29
I'm having the same problem. It's either wow or vent that have sound, but not both

---

### Post by XVampireX on 2006-09-30
OSS: Doesn't allow you to use software mixing. Meaning: Only one application will be able to use sound.

ALSA: Allows software mixing. However, the ALSA driver in wine doesn't work very well.

Fix: sudo apt-get install alsa-oss

What then?: launch your game and ventrilo via: aoss wine /path/to/file

Errr, forgot to mention that you're supposed to do it while OSS is selected in wine.

---

### Post by Chebyshev on 2006-10-02
I've got Vent installed in running, but can't get outgoing working.

I'm on a Thinkpad T22 with a Cirrus Logic CS4297A rev 4 sound device. The GSM codec is installed fine. I select the device for the ouput mixer and set Mux to rec and Line to mic. I can hear myself tapping on the mic through the speakers on the laptop, but when I hit Monitor I just get 'Abs Zero' over and over. The console says:

err:wave:OSS_OpenDevice ioctl(/dev/dsp, SNDCTL_DSP_SETTRIGGER, 3) failed (Broken pipe)

I've tried every combination of input and output to no avail and tried the above idea with alsa-oss. Any suggestions?

Edit: When I try using DirectSound for input I get in the console:

err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.

---

### Post by fakie_flip on 2006-12-05
I am getting an error about a codec. How did you install the GSM codec? Maybe I need it. I don't know what it is. Ventrilo has no sound. I am using Alsa and the newest Wine.

---

### Post by chadk on 2006-12-06
> **XVampireX said:**
> Fix: sudo apt-get install alsa-oss

This allows both to use sound then?

---

### Post by Sammi on 2006-12-06
Don't quote me on it, but I think that aoss runs oss programs through alsa, thus making them work just like regular alsa programs.
At least I am able to make Teamspeak work with sound, while playing WOW, by using aoss, and in theory this should work the same way with Ventrilo.


Like XVampireX said, one installs aoss by running this command:
```
sudo apt-get install alsa-oss
```
And then one uses it by starting the programs with the "aoss" command, something like this:
```
aoss wine /path-to-program/TeamSpeak
```
```
aoss wine /path-to-program/Ventrilo
```
```
aoss wine /path-to-program/WoW.exe
```

---

### Post by fakie_flip on 2006-12-08
> **Sammi said:**
> Don't quote me on it, but I think that aoss runs oss programs through alsa, thus making them work just like regular alsa programs.
At least I am able to make Teamspeak work with sound, while playing WOW, by using aoss, and in theory this should work the same way with Ventrilo.


Like XVampireX said, one installs aoss by running this command:
```
sudo apt-get install alsa-oss
```
And then one uses it by starting the programs with the "aoss" command, something like this:
```
aoss wine /path-to-program/TeamSpeak
```
```
aoss wine /path-to-program/Ventrilo
```
```
aoss wine /path-to-program/WoW.exe
```

I tried using aoss like this.

aoss wine .wine/drive_c/Program\ Files/Ventrilo/Ventrilo.exe

and I still get this error when I connect with Ventrilo.

"Unable to initialize outbound codec (GSM 6.10 - 11 KHz, 16 bit): Unable to find the specified codec."

---

### Post by mitchbones on 2006-12-09
I have the needed codec on my flashdrive, you are supposed to put it in one of the Windows folders. I added you to aim, I will send it to you when I see you online.

---

### Post by mitchbones on 2006-12-09
Found a solution in this post
[http://www.ubuntuforums.org/showthread.php?t=41737&highlight=ventrilo](http://www.ubuntuforums.org/showthread.php?t=41737&highlight=ventrilo)
[QUOTE=endy

5. Edit the file:
```

~/.wine/drive_c/windows/system.ini

``` 

And add the following line:
```

MSACM.msgsm610=msgsm32.acm

```

6. Next you need to get your hands on the windows file 'msgsm32.acm' from an existing windows partition (C:/WINDOWS/system32/msgsm32.acm) and copy it to  '~/.wine/drive_c/windows/system/'.

7. Run vent:
```

cd ~/ventrilo
wine ./Ventrilo.exe

```

I hope it works, and I also hope I'm didn't state the obvious  :razz:[/QUOTE]

I attached the needed System File.

---

