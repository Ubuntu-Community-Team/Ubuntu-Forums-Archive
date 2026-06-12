---
title: "Optical SPDIF-Out issues. 9.06 Jaunty (newb)"
date: 2009-04-28
forum: General Help
---

### Post by Gargamel_ on 2009-04-28
Hi, Im fairly new to Ubuntu. This is the first time i have installed it for serious use, direct to my hdd. I have used it as a vm in vmware server, but again, only as a toy. Currently my machine is configured as a tri-boot WinXPsp3 + Ubuntu + Windows 7beta, with grub as the boot loader.

Im fairly savy with computers even though im new to Linux. I do alot of work on my computer because i am a CS major, and thus its somewhat neccisary that I get some licks in with linux, at least to say i can work within it. However because i spend so much time at the keyboard I also keep alot of media on here to keep me from getting bored while scripting xml:popcorn:. 

Here is where the problem starts. I have a nice set of logitech z-5500 speakers, and it just so happens that the realtek soundboard that came with my **Abit AW9D-Max** has dolby digital SPDIF-Out, as of yet i cannot for the life of me figure out how to get this working. I might have jumped the gun in installing Jaunty as I didnt get all of this ironed out before I installed, but i think im just missing the right driver (praying there is a right driver).


Checklist:

Analog in and out via headset in windows xp  -  (WORKS)
SPDIF-Out in windows xp to z-5500 (digital and analog)  -  (WORKS)
Analog/Componant Out in windows xp to z-5500  -  (WORKS)

SPDIF-Out in Ubuntu 9.04 to z-5500 (digital and analog)  -  [broken]
Analog in and out via headset in Ubuntu 8.10-9.04  -  (WORKS)
Analog/Componant Out in Ubuntu 9.04 to z-5500  -  ...unknown?  //analog cable is currently M.I.A. and I'd rather use the SPDIF anyways.


Current Sound Configuration In Ubuntu 9.04

Sound Events: Autodetect
Music and Movies:  Autodetect
Audio Conferencing (Sound Playback): Autodetect
Audio Conferencing (Sound Capture): HDA Intel ALC883 Analog (ALSA)
Default Mixer Tracks: Realtek ALC882 (OSS Mixer)

note: tried turning all and any of the "Sound Playback" Options to "HDA Intel ALC883 Digital (ALSA)" (the only option that states it is digital) and the test gives no tone, through either the headphones or the speakers.



Ive tried to be as exhaustive as i could be but let me know if there is anything else i can add to help you help me :KS.

Thanks in Advance.

---

### Post by fooman on 2009-04-28
try installing the gnome-alsamixer.  get it from synaptic (system > administration > synaptic package manager....search for gnome-alsamixer) or open a terminal (applications > accessories > terminal) and type or copy/paste the following:

```
sudo apt-get install gnome-alsamixer
```

enter your password when prompted.  after it installs,  find and open it in applications > sound and video > gnome alsa mixer

when it opens, find the option for IEC958 and put a check next to it.

see if that works.  if it does not,  try turning *down* the slider for IEC958 P and see if that works.

hope that helps.

---

### Post by Gargamel_ on 2009-04-28
Thanks for the quick response, but when i tried the code you posted i got this error messge.

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Would booting to "safe mode" and running the script again be a better idea?


Also it might be relavent though I forgot to mention before, that i removed one of the sound drivers following instructions in another guide. Ill try to pull it again now.

---

### Post by fooman on 2009-04-28
do you have synaptic open?  if yes,  close it and try the command again.

---

### Post by Gargamel_ on 2009-04-28
Possibly, i had songbird open, could that have been the problem? Like i said, ive never really used any UNIX derivative before, i dont really know how any of these programs within Ubuntu work or interact. Either way, I closed out of everything ran that line again and it apparently downloaded and installed the mixer.

The check didnt help, and there was no slider labeled IEC958 P.

There was a box to untick (ticked by default) IEC958 Default PCM which I toggled to no avail and a Slider labeled PCM which also did nothing except turn down the volume in my headphones.

---

### Post by Gargamel_ on 2009-04-28
I got somthing to work but then it broke again. 

I opened up a flash player chatroom and it worked, I was getting sound out of the speakers, so it was getting an analog signal.

I had songbird open but as soon as I unpaused the song, hoping to hear it through the speakers they cut out and I was back down to only my headphones.

any ideas?

---

### Post by fooman on 2009-05-03
after my last post here,  i somehow lost sound through my spdif/out (not the first time).

i have managed to get it back by running this command in a terminal:

```
iecset audio 1
```

found that while browsing this bug report: 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/25632](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/25632)

---

### Post by Gargamel_ on 2009-05-05
Thanks for all the help. Today i just decided i'd had enough did a fresh install today, did all the updates b4 i installed anything else and it worked as soon as I installed the mixer. I'm not sure what the discrepentcy was tho. 

Not to sound greedy but is there a way to enable digital audio aswell? Right now its just analog SPDIF-out, which i can live with but it would be nice to get digital out since my hardware supports it. If you dont know anything about it, but ill keep looking.

Thanks for the help.

---

### Post by bergoo on 2009-05-21
Thanks alot. This worked perfectly for me.

---

### Post by nickmayfield on 2009-05-23
ok so i'm not having any luck with the alsa mixer. as i click on different IEC options I can watch my reciever with is hooked up through coax spdif go from digital to analog. all i am getting out of the speakers well was getting is crackling. i got analog sound for about 20 seconds through the spdif. so what am i doing wrong. please help. trying to make this my media center pc. thanks in advance for any help

---

