---
title: "How to fix Hardy (32bit/64bit) SATA/SOUND/MIC problems on Dell VOSTRO 1400"
date: 2008-10-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ukripper on 2008-10-02
Hardy 64bit works great on Vostro 1400, I had to only fix the following problems:

Let me start with the first notorious bug SATA drive Load/unload cycle.

_[COLOR="DarkRed"]Fixing High frequency load and unload cycle, ticking noise of SATA drive in laptop mode[/COLOR]_

[I][COLOR="Red"]Note: only for affected drives mainly on Dell laptops. Power saving mode is enabled by default on 
laptop drives which may cause high frequency load and unload cycles.[/COLOR][/I]

To check how often your drive is load cycling:
```
smartctl -d ata -a /dev/sda
```
(This command is for SATA drive only; you'll need to install the
smartmontools package first.)


Fix worked on ubuntu Gutsy and on Hardy too:

 Download this file,
[http://launchpadlibrarian.net/12024037/90-hdparm.sh](http://launchpadlibrarian.net/12024037/90-hdparm.sh)

and install as following from terminal:


If you have downloaded to desktop then in terminal type following(otherwise go to the location where you have saved the file):

```

cd ~/Desktop
```

Install using following commands:

```
sudo install 90-hdparm.sh /etc/acpi/resume.d/
sudo install 90-hdparm.sh /etc/acpi/start.d/
sudo install 90-hdparm.sh /etc/acpi/ac.d/
sudo install 90-hdparm.sh /etc/acpi/battery.d/
```


**_[COLOR="DarkRed"]VOSTRO SOUND & Internal MIC FIX[/COLOR]_**

[COLOR="DarkRed"]_Sound fix -_[/COLOR]
In terminal type: ```
gksudo gedit /etc/modprobe.d/alsa-base
```

then add option: > snd-hda-intel model=dell-3stack

save and exit, then reboot.

[COLOR="DarkRed"]_Internal MIC fix_-[/COLOR]
VOLUME CONTROL APPLET in PANEL

Double click the VOLUME CONTROL APPLET until the PREFERENCES window opens up.

Then  **EDIT –> PREFERENCES** and choose **CAPTURE** and **DIGITAL** and **DIGITAL INPUT SOURCE**.

Then **OPTIONS **should appear, just click on it (it shows **DIGITAL INPUT SOURCE**) and change the value to **DIGITAL MIC**.

This will fix the internal mic then test it in applications like skype.

If anyone knows how to fix LED of IWL3945 please post in this thread?

---

### Post by anachoret on 2009-01-02
In my case I did nothing with sound settings except change the value for Input Source to "Front Mic". After that I am able to use regular headset with either Skype or Sound_Recorder.

Seems to me the "Mic" means the microphone above the screen, but that microphone is not supported by Linux in Vostro 1400.

---

### Post by anachoret on 2010-05-09
> **anachoret said:**
> In my case I did nothing with sound settings except change the value for Input Source to "Front Mic". After that I am able to use regular headset with either Skype or Sound_Recorder.

Seems to me the "Mic" means the microphone above the screen, but that microphone is not supported by Linux in Vostro 1400.
Here is my "investigation" :)
The microphones in Vostro 1400 are working under any Ubuntu since 8.04. The trick is following.

Run the 'alsamixer', set
1."Digital" -> "Digital"
This settings activates the front microphone above the screen.

Run the 'alsamixer', set 
1."Digital" -> "Analog I"
2."Front Mi" -> "Mic In"
3.In "Sound Proferences" choose "Microphone 2" in the "Input" tab.
These settings do activating the line-in microphone below the touch pad.

---

### Post by ukripper on 2010-05-10
Everything works on vostro 1400 using 10.04LTS. This guide is obsolete for 10.04. Must be used till Jaunty 9.04 only.

---

### Post by anachoret on 2010-05-10
And finally with Lucid Lynx.

By default, an option "Microphone 1" is active and the microphone above the screen is working. Change the sound input option to "Microphone 3" and the line-in microphone below the touch pad get up and running (the front screen mic is disabled as well).

Progress! :)

---

