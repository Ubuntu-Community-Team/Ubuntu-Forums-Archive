---
title: "No sound using kernel 2.6.25 with Dell Latitude D600"
date: 2008-04-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by martinlall on 2008-04-24
Hello to all,

I'm using 8.04 LTS with kernel 2.6.25 and I don't have any sound.
I tried everything to get it to work, but no luck.

I get a lot of errors:

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

No volume control GStreamer plugins and/or devices found.

No supported PnP or PCI card found.

And so on...

But lspci shows my sound card. So how it's possible, that lspci recognizes my sound card and everything else not?


If somebody have a good idea, please share it.


Martin

---

### Post by duncanbourne on 2008-04-24
Sorry I can't help you, but I'm having exactly the same problem with my 1525n. I'm guessing lots of people are going to find this when they upgrade their Dells...
Duncan

---

### Post by konungursvia on 2008-04-24
Did you try installing the backports and rebooting?

Here is the install for the backports. Do this then reboot if you want to try my solution:

sudo apt-get install linux-backports-modules-generic

---

### Post by WBL on 2008-04-25
> **konungursvia said:**
> Did you try installing the backports and rebooting?

Here is the install for the backports. Do this then reboot if you want to try my solution:

sudo apt-get install linux-backports-modules-generic

No sound here on my 1525n...or DVD playback either.  aptitude could not find linux-backports-modules-generic.

-WBL

---

### Post by martinlall on 2008-04-25
"Couldn't find package linux-backports-modules-generic."

Any other idea?

---

### Post by martinlall on 2008-04-25
Also I don't have any mixers in Preferences -> Sound
I forgot to mention that.

Also i looked into: sudo gedit /etc/group
And i'm in audio group. And out of ideas..

---

### Post by chall32 on 2008-04-25
I have sound on my D600. All system sounds are working OK... I'm using Hardy KDE4 Kubuntu.

I have just no way of controlling the sound! The 3 buttons (volume down / volume up / mute) don't make any changes to the volume at all.

No volume indicator on task bar either.

lspci lists
```
Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
```

---

### Post by martinlall on 2008-04-25
> **chall32 said:**
> I have sound on my D600. All system sounds are working OK... I'm using Hardy KDE4 Kubuntu.

I have just no way of controlling the sound! The 3 buttons (volume down / volume up / mute) don't make any changes to the volume at all.

No volume indicator on task bar either.

lspci lists
```
Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
```

Are you using also compiled kernel 2.6.25 like me?
If not, then you may have good chance to get it to work.

Google sigmatel audio drivers and download them from official site.
That worked for me last time, with old kernel.

Also check your sound mixer settings somewhere under preferences? (or wherever they are in Kubuntu)

There are lots of forums talking about Sigmatel AC97 sound problems.
Good luck!

---

### Post by martinlall on 2008-04-28
I made bug report about this problem.
So everyone who has **sound** problems with kernel **2.6.25**, please comment your problem also.

Bug #220556

---

### Post by eamonireland on 2008-04-29
My sound problems were totally sorted by [http://ubuntuforums.org/showthread.php?t=616845]("http://ubuntuforums.org/showthread.php?t=616845")

---

### Post by martinlall on 2008-04-29
I could handle this myself if any command would show my codecs or my sound card specific information ;)

The problem is that only lspci gives only some info about my sound card, but aplay -l, alsaconf, alsamixer etc doesn't do anything :D

Basically, some of my software gets my sound card, some of it won't.
Problem is little deeper..

---

### Post by martinlall on 2008-05-01
After installing Pulseaudio I can edit the sound volume...
But no sound still..

---

### Post by mstrpete on 2012-11-24
I'm bumping this with a new wrinkle: On-board volume controls work on the built-in speakers, but not the headphone/speaker jack. Web app volume controls (ie Pandora) work on both. No volume indicator in upper status bar. 

Dell Latitude D600, 512 MB RAM, 1.4 Pentium M, running 12.04 with Xfce, don't know the kernel or where to find that info. Bought the machine with this OS pre-installed. Everything else works fine, though I've had a few interesting glitches I've been able to resolve.

P.S. fairly new to Linux. Hi there.

---

