---
title: "auto start using USB headset"
date: 2010-10-18
forum: Desktop Environments
---

### Post by Andrew Golightly on 2010-10-18
Hi all,

I have a Logitech headset. When I plug it in, Ubuntu recognises it straight away. All fine there.

If I'm using something like skype though, I have to go into System->Preferences->Sound and select my headset as the output and input.

Is there a way for it to auto start using my headset as soon as I plug it in???

thanks.

---

### Post by P4man on 2010-10-18
Install pulse audio manager:
```
sudo apt-get install paman
```

Then go to applications, sound and video, pulseaudio device chooser. That will add a tray icon. You can set default source and sink to your USB (?) headset there.

 Note that this does work, but its not reflected in the sound preferences applet which still seem to default to the soundcard, but if I set it as such in padevchooser, sound input and/or output is redirected to my usb set the moment I plug it in.

---

### Post by Andrew Golightly on 2010-10-18
thanks. Although I don't get it up to the point where I set it as the default. I've installed paman, and am looking at the options it gives me from the icon.
See attached screenshot.

---

### Post by P4man on 2010-10-18
OKay that only seems to work if you have set up a local soundserver, Im not sure if this is the easiest or best way to do it, but since it works, go to "configure local sound server" in that same menu, "network server", and enable "enable network access to local sound devies" (I suspect the other 2 arent needed in your case, I use it to stream all audio from my laptop to my desktop).

After that, you will see the options I mentioned earlier. I hope.

---

### Post by kostkon on 2010-10-18
Actually, you only need the *PulseAudio Volume Control* utility. Thus, select *Volume Control* from this menu (or PulseAudio Volume Control in your applications menu i.e. *Applications &#8594; Sound & Video &#8594; PulseAudio Volume Control*), then start Skype, make a call and you should see its input and output audio streams in the *Playback* and *Recording* tabs. Just select the device you want for these streams. PulseAudio will remember your choices, so you only need to do this once.

---

### Post by P4man on 2010-10-18
> **kostkon said:**
> Actually, you only need the *PulseAudio Volume Control* utility. Thus, select *Volume Control* from this menu (or PulseAudio Volume Control in your applications menu i.e. *Applications &#8594; Sound & Video &#8594; PulseAudio Volume Control*), then start Skype, make a call and you should see its input and output audio streams in the *Playback* and *Recording* tabs. Just select the device you want for these streams. PulseAudio will remember your choices, so you only need to do this once.

Right, but then if you connect the headset after skype started,  does it actually switch the sound output (and input) to the headset? I thought not, but I could be wrong, and if so, then thats definitely an easier solution.

---

### Post by Andrew Golightly on 2010-10-18
> **kostkon said:**
> Actually, you only need the *PulseAudio Volume Control* utility. Thus, select *Volume Control* from this menu (or PulseAudio Volume Control in your applications menu i.e. *Applications &#8594; Sound & Video &#8594; PulseAudio Volume Control*), then start Skype, make a call and you should see its input and output audio streams in the *Playback* and *Recording* tabs. Just select the device you want for these streams. PulseAudio will remember your choices, so you only need to do this once.

How do I select the input device being my headset from this screen??

---

### Post by kostkon on 2010-10-19
> **Andrew Golightly said:**
> How do I select the input device being my headset from this screen??
To set your headset as the input device for Skype (and only for Skype), click the *Recording* tab, and then start a call in Skype. You'll figure out the rest easily.

---

### Post by boris.abramov on 2012-09-09
A bit easier one, for Unity users.
[http://files.suntrail.org/soundswitch/soundswitch-2.0.deb](http://files.suntrail.org/soundswitch/soundswitch-2.0.deb)

---

### Post by wildmanne39 on 2012-09-09
Thanks for sharing. Thread Closed.

---

