---
title: "identifying sound devices used by skype?"
date: 2009-05-01
forum: General Help
---

### Post by aquascrotum on 2009-05-01
When I load skype I'm having difficulty getting my mic to work.

In the list of available audio devices I have no idea which one is which.

Sound In options are:

Default Device
HDA Intel (hw;INtel, 0)
HDA Intel (plughw:Intel,0)
hdmi
headset
pulse

My PC has a built in sound card with 5.1 outputs and line in to the rear panel, and a headphone and mic extension to the front panel.

Ive tried all combos with both line-in points but none are working. Speakers are working fine under Sound Out option "HDA INtel (hw;Intel,0).

Any ideas would be welcome. And the mic is tested and working under winxp.

---

### Post by soro2005 on 2009-05-01
Is it an internal mic? Unfortunately, Skype is a bitch when it comes to this. It's a perennial problem, and people have made varying mileage.

Also, does the sound system in general recognize the mic?

---

### Post by aquascrotum on 2009-05-02
No, external mic plugged into one of 2 mic-in jack points as described.

How would I test that the sound system in general recognises the mic? Sound recorder or something?

**Edit - yeah I tried sound recorder, it reognised the mic and recorded on channel "HDA Intel STAC92xx".

---

### Post by dsavi on 2009-05-02
I've also had some pretty... Funky problems when it comes to Skype and sound. What I know is this: Skype (Still) uses OSS, and you need to have the ALSA OSS emulation layer to use it if you want ALSA. Ok, honestly I suck at Linux and sound- So have a look at this page. It might help you.
[http://www.skype.com/help/guides/soundsetup_linux.html](http://www.skype.com/help/guides/soundsetup_linux.html)

---

