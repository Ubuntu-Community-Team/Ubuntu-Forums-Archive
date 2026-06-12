---
title: "No sound comming from A7N8X-E Deluxe motherboard"
date: 2006-07-25
forum: Desktop Environments
---

### Post by xyuri on 2006-07-25
I have the motherboard mentionted in the title with has the Nforce2 (via?) chipset which has onboard sound. This seems to be detected by ubuntu desktop, but I do not hear any sound.

If anyone would like to help me resolve this issue then the following might also be of interest ...

I enabled the post-reporter when the machine boots up and expected a voice basically giving the "a-ok" ? no such sound ... is there surposed to be? The speakers I am using are being used by my current desktop, so they work fine ... but maybe the sound card is broken?

Any input is greatly appreciated. Thank you :)

---

### Post by xyuri on 2006-07-25
I have tried googling this btw... a few people have had the same problem but none of them mentioned a solution.

Anybody?

---

### Post by lerrup on 2006-07-26
I have a similar board - and it would only produce sound from the headphone jack and not the line out until I solved the problem.

Have you tried enabling sound using the sound configuration app in the sysytem menu?  I had 2 options and choose the nvidia option - it then worked!

I would be more specific, but I got mine to work in XFCE...

Also - its not muted automatically, is it?

---

### Post by autocrosser on 2006-07-26
First thing I would do --if you have Alsa Mixer or Gnome Alsa Mixer installed--check & see if anything is muted by default--if so, un-mute it & see what happens--If you don't have a mixer--get one--I've been using Gnome's mixer & it works ok--I've got a Asus P5P800-VM & some of the onboard stuff was mute by default--unmuted--it works ok..

My two cents--hope it helps;)

---

### Post by xyuri on 2006-07-26
Thank you both for your input :)

These are my sound options at the moment:
[http://img102.imageshack.us/img102/615/screenshotvolumecontrolnvidianforce2alsamixeryi4.png](http://img102.imageshack.us/img102/615/screenshotvolumecontrolnvidianforce2alsamixeryi4.png)

I have already tried the microphone jack and it also produces no sound :confused:

---

### Post by autocrosser on 2006-07-26
Get rid of Alsa Mixer & Get Gnome Alsa mixer--has more options & might do what you need--My shot of Gnome Mixer---

Go into preferences & select what looks like it will work for you--I think if you play with it a bit you'll get it---Keep your fingers crossed!!!:D

---

### Post by xyuri on 2006-07-26
How do i get rid of one and install the other? I am looking in the synaptic package manager but dont see any of this. (sorry, i am noob).

---

### Post by autocrosser on 2006-07-27
You need to enable the extra repositories--lots of posts about that---

---

### Post by xyuri on 2006-07-30
I am still not getting any sound from any ports.

Could someone with the same motherboard please tell me whether the POST reporter is surposed to say anything when the system starts without any errors?

---

### Post by Sendervictorius on 2006-07-30
I have an A7N8X motherboard, and my sound has stopped too. It works fine under breezy (still), and also worked on dapper when I installed from CD. Since then it has stopped on dapper.

I suspect a repository update has done something. I normally run with the sound off, so I'm not that concerned, and didn't notice exactly when it stopped. I'm curious to see if this is a wider issue that the usual "un-mute" advice won't fix.

---

### Post by xyuri on 2006-07-30
Might just have to find a space PCI sound card and try that.

Thank you all for your help, but I think this issue remains unresolved ;)

---

### Post by Sendervictorius on 2006-07-31
> **xyuri said:**
> Might just have to find a space PCI sound card and try that.

Thank you all for your help, but I think this issue remains unresolved ;)

I just tried booting off the dapper live CD, and my sound works. Maybe worth a quick try before instaling that spare card.

---

### Post by flummoxed on 2007-05-15
My friend has the same mobo, and no sound is coming out of his either. I tried to fix it, but failed. I'm now in the market for an old pci sound card...

---

### Post by cudjoe on 2008-03-01
Which release are you guyz using ?

This motherboard is a couple of years old, and quite common.
Any news about Hardy, which uses a new sound system ?

I see nothing in Launchpad, and the Wiki page is very old :
[https://wiki.ubuntu.com/Asus_A7N8X_Deluxe](https://wiki.ubuntu.com/Asus_A7N8X_Deluxe)

Thanks !

---

