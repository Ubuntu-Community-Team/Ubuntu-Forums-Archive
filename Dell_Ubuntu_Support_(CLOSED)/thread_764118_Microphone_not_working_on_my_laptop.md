---
title: "Microphone not working on my laptop"
date: 2008-04-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Sk1nnyMan on 2008-04-23
Hey I just bought my Dell Inspiron 1525 with Vista preinstalled, I then installed Ubuntu in a dual boot configuration from the standard LiveCD.

Currently the only thing I have found that doesn't work on Ubuntu is the internal microphone. Any time I record from anything all I get is silence.

In the System > Preferences > Sounds if I set the Sound Capture combo box and set it to anything but Test Sound or Silence and hit Test I get an error message saying: 
"Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat"

If I go into the System > Preferences > Sounds and set the Sound Capture to Test Sound then I can record the beep in audacity or as an audio track on cheese or whatever.

When I tried to install the backport drivers the sound stops working (I can get it back by removing the drivers) and the microphone still doesn't work with the same symptoms.

The microphone does work in Vista.

Any help will be appreciated.

---

### Post by ethanay on 2008-04-24
check out Dell's [Ubuntu wiki]("http://linux.dell.com/wiki/index.php/Products/Consumer")

specifically, the "known issues" section

haven't tried the solution, but i am just waiting for Hardy b/c i hear that it's resolved by default w/it

---

### Post by niteshifter on 2008-04-24
Hi,

> Currently the only thing I have found that doesn't work on Ubuntu is the internal microphone. Any time I record from anything all I get is silence.

Known issue as ethanay stated. This link will take you direct to the Known Issues for 7.10 [http://linux.dell.com/wiki/index.php/Ubuntu_7.10#Known_Issues]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10#Known_Issues")

I have a 1420n - #9 on the list (Built In Digital Mic ...) worked for me, my microphone did work after implementing the fix. This fix will also require new software for the built-in modem - I applied it but I do not know if it works (have never used the modem, before or after fixing).

What the microphone fix does is give you a properly configured ALSA (audio) driver. Like I said above, it fixed the internal mic issue - and some other audio issues I had (no capture with Audacity, for example).

---

### Post by vandorjw on 2008-08-03
easier fix than downloading new files is

open terminal and type "alsamixer"

then use arrow keys to move over to the far right, and use the up-down arrows to change from analog to "digital"

press escape.

Microphone works now :)

Cheers - CC7

---

