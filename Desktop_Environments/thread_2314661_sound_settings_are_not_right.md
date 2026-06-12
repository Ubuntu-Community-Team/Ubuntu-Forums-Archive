---
title: "sound settings are not right"
date: 2016-02-22
forum: Desktop Environments
---

### Post by danielsender on 2016-02-22
I'm running 14.04.3 (64b) on a Dell M90 laptop. The problem I'm having is that the "Sound Settings" window cannot remember what I set. It used to work OK but I don't remember when this problem appeared. To be more precise, I have like 3 different options for input devices, from top to bottom on the list: "Analog Input - Built-in Audio" , "Microphone - 1.1 root hub" and "Microphone - 081a" . I want to use the second one so I clicked there and it works as long as I keep that window open, but if I close it the choice goes back to the first choice. I have another machine (32b) also with 14.04.3 and it doesn't show this behaviour.

Thanks in advance.

Daniel

---

### Post by danielsender on 2016-02-23
bump

---

### Post by danielsender on 2016-02-29
I looked into the folder *~/.config/pulse/36b92cb9019d00873fa5e5a65671c61d-default-source* and observed that its entry changes when I click on the different input options, however it goes back to the first of the list when I close the settings window. So for example when I open the setting window I read in that file:

[I]alsa_input.pci-0000_00_1b.0.analog-stereo

[/I]after clicking on the desired option y read in the same file:

*alsa_input.usb-FORTEMEDIA_FM1083-00-FM1083.analog-mono*

When I close the settings window the line will change back to the first line.

Thanks in advance.

---

