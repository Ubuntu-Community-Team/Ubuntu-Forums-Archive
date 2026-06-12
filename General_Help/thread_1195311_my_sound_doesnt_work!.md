---
title: "my sound doesnt work!"
date: 2009-06-23
forum: General Help
---

### Post by kmaster228 on 2009-06-23
hey all recently i was tweaking with the volume and sound settings for my playback and recording volumes but after i restarted my computer my sound on my internet doesnt work but it works when im using amarok to play music and i dont know what is happening
btw i use my webcam to record sound through its inbuilt mic
please help i included screen shots to help 
[ATTACH]118721[/ATTACH]
[ATTACH]118722[/ATTACH]

---

### Post by kostkon on 2009-06-23
OK, it first of all, could you open a terminal and give
```
aplay -l
```
and post the output here?

---

### Post by philcamlin on 2009-06-23
all i had to do was sudo apt-get update and sudo apt-get upgrade 

my sound worked after that :popcorn: hope it does for you

go to the volume thing up in the toolbar and change every thing to 100%

---

### Post by kmaster228 on 2009-06-23
ok heres the result of aplay -l and ill try update and upgrade
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by kostkon on 2009-06-23
OK, try this. Go to *System &#8594; Administration &#8594; Users and Groups*, select your username, press *Properties* and then in the *User Priviledges* tab enable the *Use sound devices* option.

Or from the terminal you can do it like this
```
sudo adduser yourusername audio
```
whereas *yourusername* means the user name that you have in your system.

Hope that helps.

---

### Post by kmaster228 on 2009-06-23
it was aldready checked
 btw does this help?

cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xe3220000 irq 22
 1 [U0x46d0x9a1    ]: USB-Audio - USB Device 0x46d:0x9a1
                      USB Device 0x46d:0x9a1 at usb-0000:00:1a.7-4, high speed
1 is my webcam

---

### Post by kmaster228 on 2009-06-23
again its strange i quit amarok i closed firefox and when i clicked test sound its works then open firefox and no sound but amarok plays music

---

### Post by kostkon on 2009-06-23
> **kmaster228 said:**
> it was aldready checked
 btw does this help?

cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xe3220000 irq 22
 1 [U0x46d0x9a1    ]: USB-Audio - USB Device 0x46d:0x9a1
                      USB Device 0x46d:0x9a1 at usb-0000:00:1a.7-4, high speed
1 is my webcam
Aha, hmm. Try this:
Install the *PulseAudio Device Chooser* (using *Synaptic*). You need to run it, left-click on its icon in your system tray and select the *Volume Control*.

Then, you will need to select the *Output Devices* tab and you should see your Intel sound card listed there along with the unknown USB device. Right-click on your Intel's entry and enable the *Default* option to set it as the default output device in your system.

---

### Post by kostkon on 2009-06-23
> **kmaster228 said:**
> again its strange i quit amarok i closed firefox and when i clicked test sound its works then open firefox and no sound but amarok plays music
OK. Make sure that your sound playbacks in your sound preferences (i.e. *System &#8594; Preferences &#8594; Sound*) are set to *Autodetect*.

Also, if you don't get sound in *Firefox* (i.e. in *Flash* videos and such), put a *Flash* *Youtube* video playing, for example, and then in the *PulseAudio* volume control select the *Playback* tab. You should see the audio stream of the *Flash* video there. Right-click on it and select *Move Stream...* and in the list that will appear select your *Intel* card.

---

### Post by kmaster228 on 2009-06-23
the only output device there is is null ouput and when i play youtube vids i see the audio stream but the only place to move it is null out put...
ok do you want to have remote control cause im willing

---

### Post by kmaster228 on 2009-06-23
Bump - doesnt any body have a clue? i am willing to let people use remote acontrol

---

