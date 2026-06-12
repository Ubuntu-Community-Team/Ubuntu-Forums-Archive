---
title: "No sound from USB headset"
date: 2009-06-19
forum: General Help
---

### Post by John M2009 on 2009-06-19
I cant get any sound. Since I lost the driver disc for my mother board, I have been using a logitech USB headset, which does not seem to work with Ubuntu for some reason.  It recognises it ok,  its in the list of sound devices in preferences (one of the first things i checked) and im pretty sure its not a problem with the USB ports, as Ubuntu can see my pen drive and my USB mouse fine.

I liked windows when everything would just work,  well,  most of the time anyway lol

---

### Post by redilyn on 2009-06-19
Have you checked your volume control to see if it is turned up and not muted?

Check Main volume, PCM, and headphone if you have them

---

### Post by kostkon on 2009-06-19
You can make them to work easily, don't worry.

Assuming that you have a version of Ubuntu >= 8.10

First of all, since you changed them, you need to put your sound playbacks in your sound preferences (i.e. *System &#8594; Preferences &#8594; Sound*) back to *Autodetect*.

Then you need to install the *PulseAudio Device Chooser* utility using *Synaptic*. You need to run it, left-click on its icon in your system tray and select the *Volume Control*.

Next, you will need to select the *Output Devices* tab, right-click on your headset's entry there and enable the *Default* option to set them as the default output device in your system.

For more info, check [this helpful thread here]("http://ubuntuforums.org/showthread.php?t=1130384").

---

### Post by John M2009 on 2009-06-19
Ok,  I have downloaded and extracted Synaptic and Pulse Audio Device Chooser,  but I cant work out how to install either of them, before I used package manager,  which if i remember correctly.  extracted and installed the apps pretty much without me having to do anything...but it does not appear to be the case with these two.

---

### Post by kostkon on 2009-06-19
> **John M2009 said:**
> Ok,  I have downloaded and extracted Synaptic and Pulse Audio Device Chooser,  but I cant work out how to install either of them, before I used package manager,  which if i remember correctly.  extracted and installed the apps pretty much without me having to do anything...but it does not appear to be the case with these two.
But, *Synaptic* is the package manager! You can access it from *System &#8594; Administration &#8594; Synaptic Package Manager*.

In *Synaptic*, press the *Search* button and search for *PulseAudio Device Chooser* and then install this package.

---

### Post by John M2009 on 2009-06-19
Ok,  i've installed it (I think) but cant find it in my applications list,  does this mean it isnt installed or am i looking in wrong place?

---

