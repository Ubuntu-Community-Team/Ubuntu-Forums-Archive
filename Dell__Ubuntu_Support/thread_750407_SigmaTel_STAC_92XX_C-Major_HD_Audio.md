---
title: "SigmaTel STAC 92XX C-Major HD Audio"
date: 2008-04-09
forum: Dell  Ubuntu Support
---

### Post by adeel-azmat on 2008-04-09
Hi guys,
I'm a new user to linux using Ubuntu (Gutsy) 7.10
I have a Dell Vostro 1500 laptop and all seems to be fine but the sound. The inbuilt card is STAC 92XX C-Major HD Audio. I have been reading over a 100 forums and still cannot find the right solutions.

When i go to System->Pref->Sounds, I have selected ALSA in all the fields, and when i click on Test it says "gconfaudiosink: Could not open resource for writing". When i double click on the sound icon in the panel, i get the message "No volume control GStreamer plugin / devices found"

Please help! I want to stop using Windows and shift here permanently.

Rgds,
Adeel

---

### Post by Andy Mack on 2008-04-11
Try this

sudo nano /etc/modprobe.d/alsa-base

Add
options snd-hda-intel model=laptop

restart

Worked on mine

---

### Post by StevenBirnam on 2008-04-24
I have no audio on my desktop install of Ubuntu Gutsy.

Tried everyting.

Ran Alsa device test and got back: Failed to construct test pipeline for 'gconfaudiosrc !
audioconvert ! audioresample 1 gconfaudiosink profile=chat'
No idea where to go now - anybody have a suggestion?

StevenBirnam

---

### Post by expatal on 2008-05-22
> **StevenBirnam said:**
> I have no audio on my desktop install of Ubuntu Gutsy.

Tried everyting.

Ran Alsa device test and got back: Failed to construct test pipeline for 'gconfaudiosrc !
audioconvert ! audioresample 1 gconfaudiosink profile=chat'
No idea where to go now - anybody have a suggestion?

StevenBirnam
StevenBirnam (in reply to #3),

Three weeks is a long time in Ubuntu. But just in case you haven't yet seen it, this might help:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

(I have similar sound hardware on my XPS M1330 running under Gutsy, which is why I noticed your post.)

---

### Post by gkumar21 on 2008-05-25
I'm an absolute beginner in Ubuntu and Linux.I too have a Dell Vostro 1500 with Integrated Webcam and Nvidia graphics card with SIgmatel STAC 92xx device. I had the following problems 

1. WiFi wouldnt turn on and so I did a hardware upgrade where ubuntu installed proprietary drivers for Broadcom 4315 and it started working just perfect(phew!)

2. I also had problems with Nvidia card and that too was resolved by the proprietary driver solution.

3.**The third and the most shocking problem was that of the Sigmatel Audio drivers. Firstly, the sound card was detected as High Definition Audio-Intel.But I have a Sigmatel STAC9205 in my laptop which works very fine in Windows.I couldnt find any convincing posts in the forums and so I changed the sound preferneces to show STAC 92xx. I thought everything sounded fine but the volume wasnt that high as I used to get on windows.Further more to add to my woes, The sound capture was just static. Absolutely nothing.Even the ALSA architecture wouldnt work.My inbuilt digital microphone wouldnt work even after I unmuted it.I'm too much in love with Ubuntu and I cant let this issue to ruin the impact that Ubuntu has had on me.Please give me some suggestions and solutions.**


Grazie!

---

### Post by gkumar21 on 2008-05-26
I just found out that the ALSA does not have the device drivers for Sigmatel STAC 9250 device that is there on my laptop..Looks like I'll have to wait till it is posted.

---

### Post by lbowersmks on 2008-06-10
I've been searching for a solution to the Sigmatel STAC 9250 problem myself with a Gateway NX560XL laptop.  Everything works for me except the mic.  Hopefully the Alsa site will have a driver soon!

---

### Post by catonano on 2008-06-25
Hello people,

> **lbowersmks said:**
> I've been searching for a solution to the Sigmatel STAC 9250 problem myself with a Gateway NX560XL laptop.  Everything works for me except the mic.  Hopefully the Alsa site will have a driver soon!

I was wondering wether the page at [this link]("http://ankurjain.org/2007/11/03/ubuntu-gutsy-microphone-problem-on-dell-inspiron-1520/") is pertinent.

I have the same problem, on a Dell Vostro 1700 with the SigmaTel STAC9205 chip.

It's an office machine so skype usage is goinna be quite important. I tried to install Ubuntu but I hadn't considered this possibility :-(

Thanks for any help
Cato

---

### Post by lbowersmks on 2008-06-25
Those settings look a little different than my 9250, but I will give it a try soon.  The best advice I have received is to either get a usb microphone or a webcam with a built in mic compatible with skype and linux.  Here's a link for that: [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

Hope this helps.

---

### Post by adeel-azmat on 2008-06-25
Thats good!

At the end I just re-installed the latest version of Gutsy Gibbon and alls working fine now!!

-Adeel

---

### Post by catonano on 2008-06-29
> **lbowersmks said:**
> Those settings look a little different than my 9250, but I will give it a try soon.  The best advice I have received is to either get a usb microphone or a webcam with a built in mic compatible with skype and linux.  Here's a link for that: [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

Hope this helps.

A USB microphone would be good. The list is a bit freightening. All those cams, for some of them I don't see if they have a built in mike.

A microphone like [this]("http://www.amazon.com/Logitech-980186-0403-USB-Desktop-Microphone/dp/B00009EHJV") would be wonderful.

I know, I'm a bit picky, but may I ask you if you know of a USB mike that _just works_ ?

I opened a new thread about this, [here]("http://ubuntuforums.org/showthread.php?t=844478").

Thanks anyhow
Bye
Cato

---

