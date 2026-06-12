---
title: "Gutsy~why is totem broken?!?!?!"
date: 2009-02-09
forum: General Help
---

### Post by KEE on 2009-02-09
i had to do a reinstall gutsy from fresh and find out that totem has a failure rate of 100%  upon opening!please i tried all the gstreamers and everything i can do. i need help now. please help

---

### Post by kostkon on 2009-02-09
First of all, try to run it from the terminal to see what error messages you'll get...

---

### Post by KEE on 2009-02-09
> **kostkon said:**
> First of all, try to run it from the terminal to see what error messages you'll get...
```
sudo totem
```
i get ```
(totem:13696): GLib-GObject-WARNING **: cannot register existing type `GstRTPBin'

(totem:13696): GStreamer-CRITICAL **: gst_element_register: assertion `g_type_is_a (type, GST_TYPE_ELEMENT)' failed
sh: jackd: not found


```

---

### Post by KEE on 2009-02-09
Please help

---

### Post by kostkon on 2009-02-09
Why with *sudo*? To be sure just run it like this
```
totem
```

---

### Post by KEE on 2009-02-09
> **kostkon said:**
> Why with *sudo*? To be sure just run it like this
```
totem
```

```
totem
```

i get ```
sh: jackd: not found

```

---

### Post by kostkon on 2009-02-09
> **KEE said:**
> ```
totem
```

i get ```
sh: jackd: not found

```
That's not a fatal error.

Better test it by telling it to play a file, e.g.
```
totem yourfile.mp3
```
and see what errors you'll get.

---

### Post by lavinog on 2009-02-09
have you tried installing jackd?
it looks like totem is configured to use jack and not alsa (i dont think pulse was available in gutsy) and jack is not installed.

Why are you using gutsy?

---

### Post by KEE on 2009-02-09
and its not not just totem, its every video and audio player i can find in add/remove synaptic package manager. also my firefox freezes when i go to anywhere that uses flash player. really suks this all worked great today untill i had to reinstall gutsy .  please help

---

### Post by kostkon on 2009-02-09
> **lavinog said:**
> have you tried installing jackd?
it looks like totem is configured to use jack and not alsa (i dont think pulse was available in gutsy) and jack is not installed.

Why are you using gutsy?
No, it's just a dependency error. It's not something serious. There is already a bug report about this.

But it's just a warning, nothing more...

---

### Post by KEE on 2009-02-09
> **lavinog said:**
> have you tried installing jackd?
it looks like totem is configured to use jack and not alsa (i dont think pulse was available in gutsy) and jack is not installed.

Why are you using gutsy? how do i do that? im useing gutsy i have issues with the installation with hardy. i keep getting a system32 folder that takes all my memory and i cant delete it. i think cause its not installing properly. i tried like hundreds of times. i just give up on hardy and intrepid

---

### Post by KEE on 2009-02-09
> **kostkon said:**
> No, it's just a dependency error. It's not something serious. There is already a bug report about this.

But it's just a warning, nothing more... well its making everything that has to do video/audio and any flash plugin not work at all or freezes the whole program then i have to kill it.

---

### Post by kostkon on 2009-02-09
> **KEE said:**
> well its making everything that has to do video/audio and any flash plugin not work at all or freezes the whole program then i have to kill it.
I don't think that is the reason of your problem. 

I also get this error message. You can see [the bug report]("https://bugs.launchpad.net/ubuntu/+source/gstreamer/+bug/154028") for yourself to understand that it's just harmless warning.

Now about your problem, it looks like you have a problem with your sound configuration that causes all the programs to not work or crash.

First of all, could you please post here the output of
```
aplay -l
```

---

### Post by KEE on 2009-02-09
> **kostkon said:**
> I don't think that is the reason of your problem. 

I also get this error message. You can see [the bug report]("https://bugs.launchpad.net/ubuntu/+source/gstreamer/+bug/154028") for yourself to understand that it's just harmless warning.

Now about your problem, it looks like you have a problem with your sound configuration that causes all the programs to not work or crash.

First of all, could you please post here the output of
```
aplay -l
```

```
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by lavinog on 2009-02-09
> **KEE said:**
> im useing gutsy i have issues with the installation with hardy. i keep getting a system32 folder that takes all my memory and i cant delete it. i think cause its not installing properly. i tried like hundreds of times. i just give up on hardy and intrepid

system32 is a windows folder that is frequently attacked by malware.
It appears that your system was infected.
I can't help but notice that your post about the system32 issue is on the same day you were requesting help installing limewire in wine.
Many of the infected computers that I have come across have limewire installed.

I would recommend installing clamav (antivirus) for good measure.

Also for your video issue, you might like to try vlc player. It plays just about everything.

---

### Post by KEE on 2009-02-10
> **lavinog said:**
> system32 is a windows folder that is frequently attacked by malware.
It appears that your system was infected.
I can't help but notice that your post about the system32 issue is on the same day you were requesting help installing limewire in wine.
Many of the infected computers that I have come across have limewire installed.

I would recommend installing clamav (antivirus) for good measure.

Also for your video issue, you might like to try vlc player. It plays just about everything.
thanks :) its also frostwire to since i reinstalled had everything going perfect then i add frostwire started down load a video and now nothing works again lol 
icant watch video 
icant play mp3,ogg or anything
icant use java of any kind
icant use adobe flash for anything
my harddrive becomes "read only" and I loss permission to change that  
everything seems to get broken or hacked. im lossing hope in ubuntu,

---

### Post by KEE on 2009-02-10
> **lavinog said:**
> system32 is a windows folder that is frequently attacked by malware.
It appears that your system was infected.
I can't help but notice that your post about the system32 issue is on the same day you were requesting help installing limewire in wine.
Many of the infected computers that I have come across have limewire installed.

I would recommend installing clamav (antivirus) for good measure.

Also for your video issue, you might like to try vlc player. It plays just about everything.
ha no good. my com is hacked so bad and i just installed today lol 
when i try to install clamav i get this error in spm ```
Please insert the disk labeled:
Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)
in drive /cdrom/
``` did it my drive is trying to burn the disc or spinning it at a high rate for like 20mins (i stopped it) take it out and its super hot. ubuntu is super not the safest anymore

big thanks though

---

### Post by KEE on 2009-02-10
ok i got it to work but, it didnt do anything really i still have all the same problems. lol do i really need reinstall AGAIN lol i miss winxp :( this  making me go back to windows....

---

### Post by lavinog on 2009-02-10
> **KEE said:**
> ha no good. my com is hacked so bad and i just installed today lol 
when i try to install clamav i get this error in spm ```
Please insert the disk labeled:
Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)
in drive /cdrom/
``` did it my drive is trying to burn the disc or spinning it at a high rate for like 20mins (i stopped it) take it out and its super hot. ubuntu is super not the safest anymore

big thanks though

You should remove the cd from your repositories and use the net if possible...this way you wont need to use a cd to install programs.

Ubuntu is only as safe as the user using it.
running programs as the super user defeats all of the security that is in place. You should not be using sudo to run programs unless you know that they need it. (referring to how you ran totem with sudo)
The many malware designed for windows, will most likely work with wine.
If you are using ubuntu like windows, it is likely not going to be as secure as you think it is.
In April, Gutsy will no longer be supported, and therefore security exploits will not be patched.
I suggest that you consider upgrading soon.

BTW: It appears that your problems with intrepid were caused by limewire.

---

