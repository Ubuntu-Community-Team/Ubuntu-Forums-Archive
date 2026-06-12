---
title: "pulseaudio microphone problems"
date: 2009-06-07
forum: General Help
---

### Post by ncanna1 on 2009-06-07
I recently started using skype, but cannot get my microphone to work on jaunty.  I was using esound, but reinstalled pulse because I thought that it would be easier to fix since there is so much help around for it.  I've tried fooling around with volume control and everything and I can't seem to get the microphone to work at all.  If anyone has any ideas, please help.

---

### Post by soltanis on 2009-06-07
Downgrade to ALSA. I believe Skype uses ALSA as its audio medium, and pulseaudio doesn't share resources very well.

---

### Post by Chronon on 2009-06-07
Hi.  I haven't had any luck getting Skype to use Pulse for recording/input either.  Instead of pulse I select "HDA Intel (hw:Intel,0)" on my netbook and it works.

Sound In: HDA Intel (hw:Intel,0)
Sound Out: pulse
Ringing: pulse

---

### Post by ncanna1 on 2009-06-07
It's not a skype issue, though.  I can't get input from my mic globally.

---

### Post by rabdoel on 2009-07-10
same problem here 

cannot use mic locally and neither in skype. I have messed arround with sound settings in the sound control panel (turned all volumes riht up) and can place the skype test call now and can hear myself. however gnome-sound-recorder nor skype record.

I am going to try and remove pulse audio using synaptics and then test it using the default alsa sound system.

one problem , when I try to uninstall pulse audio it shows that ubuntu-desktop needs to be uninstalled as well. I am aware that this is a kind of a meta package and should cause no problems if I remove it . can anybody verify this ?

---

### Post by omunozsj on 2010-01-13
On a HP tx1220us, Karmic, you can't access important settings through Volume Control GUI (like ATAPI MIC). Instead you need to use alsamixer from a command line terminal:

% alsamixer -V all

Hope it helps...

---

