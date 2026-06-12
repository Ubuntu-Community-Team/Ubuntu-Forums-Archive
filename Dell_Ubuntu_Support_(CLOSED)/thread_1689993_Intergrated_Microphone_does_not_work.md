---
title: "Intergrated Microphone does not work"
date: 2011-02-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by newbuntu111 on 2011-02-17
I am currently running Ubuntu 10.10 dual booting Windows 7 through wubi.
I have a Dell Vostro 2510 which is quite a rare build, but it has very similar hardware with its Vostro family laptops.

This is what i get when I do the lsusb command:
```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 1058:1021 Western Digital Technologies, Inc. 
Bus 002 Device 002: ID 1a40:0101 TERMINUS TECHNOLOGY INC. USB-2.0 4-Port HUB
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:63e0 Microdia Sonix Integrated Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```AlsaMixer 1.0.23 is installed
Card: HDA Intel
Chip: Realtek ALC268

On Sound Preferences, the only input device is Internal Audio Analog Stereo 

I've been googling for 2 days now and I have found various solutions, but none of them proved worthy :(
Any help is appreciated.

---

### Post by newbuntu111 on 2011-02-19
bump

---

### Post by mikewhatever on 2011-02-19
Make sure the mic is not muted. It's in the Input tab in the sound preferences.

---

### Post by newbuntu111 on 2011-02-19
My microphone doesn't even appear as an input device :(
The only device that shows is Internal Audio Analog Stereo and that isn't muted either.

---

### Post by mikewhatever on 2011-02-19
I also have 'Internal Audio Analog Stereo' in the input tab, but the internal mic works.
There are several alsa config options for alc268: 
less /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz
```

ALC267/268
==========
  quanta-il1    Quanta IL1 mini-notebook
  3stack        3-stack model
  toshiba       Toshiba A205
  acer          Acer laptops
  acer-dmic     Acer laptops with digital-mic
  acer-aspire   Acer Aspire One
  dell          Dell OEM laptops (Vostro 1200)
  zepto         Zepto laptops
  test          for testing/debugging purpose, almost all controls can
                adjusted.  Appearing only when compiled with
                $CONFIG_SND_DEBUG=y
  auto          auto-config reading BIOS (default)


```

Not really sure which one is for you. Try 'dell', in other words, add
**options snd-hda-intel dell** to /etc/modprobe.d/alsa-base.conf and reboot.

---

### Post by newbuntu111 on 2011-02-20
Adding that line caused the audio icon to go "--"
All audio failed and only "Dummy" was set to output.

I will be trying all the options.... there are so many that say "dell" and "dell laptops": 
:(

EDIT: I just realised that the only options that work are the ones you posted....
Anyhow, the line suggested still does not work >.<

EDIT2:
I reread your posts and I think we have a misunderstanding
>  			 		   		 		 		I also have 'Internal Audio Analog Stereo' in the input tab, _but the internal mic works_.
I am not looking to get my **internal** mic working. I'm trying to get my **integrated **microphone working. Like the kind thats mounted next to the webcam on top of the laptop.

---

### Post by PaulReaver on 2011-02-20
what about alsamixer?

---

### Post by newbuntu111 on 2011-02-20
> **PaulReaver said:**
> what about alsamixer?
Sorry, I don't understand >.<
I'm very new to Ubuntu.
I have AlsaMixer 1.0.23 installed.

---

### Post by mikewhatever on 2011-02-20
I think I got that option line wrong - should be **options snd-hda-intel model=dell** - also edited above.
...and just to restate, there is only 'Internal Audio Analog Stereo' in the input tab, and yes, the built in mic, the one next to the webcam, works.

---

### Post by newbuntu111 on 2011-02-20
Okay everything works fine with that line except the microphone again....
>.<

I tried testing with Sound Recorder and Skype and neither recorded anything.

---

### Post by newbuntu111 on 2011-02-20
YES FINALLY I GOT IT TO WORK. >.<

I used **options snd-hda-intel model=acer-dmic**
I then went to Sound preferences and switched the Connector to Microphone 2. Everything works great now :D

Thank you so much for all the help and support.

---

### Post by mikewhatever on 2011-02-20
Congrats, and thanks for the update.

---

