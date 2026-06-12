---
title: "Mini 10v no microphone"
date: 2009-06-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sefokuma on 2009-06-18
I have installed 9.04 on mi mini10v and i don't get put it ok. I don't know if this if for pulseaudio, or alsa... I have sound working but nothing program run my microphone...

Thanks.

---

### Post by nipponeon on 2009-06-18
> **sefokuma said:**
> I have installed 9.04 on mi mini10v and i don't get put it ok. I don't know if this if for pulseaudio, or alsa... I have sound working but nothing program run my microphone...

Thanks.
Instructions for activating the microphone on the mini 9 can be found [here]("http://www.ubuntumini.com/2009/04/skype-on-dell-mini-9.html") . As the hardware of the mini 10v is practically the same, I suppose this works for you too.

---

### Post by sefokuma on 2009-06-18
> **nipponeon said:**
> Instructions for activating the microphone on the mini 9 can be found [here]("http://www.ubuntumini.com/2009/04/skype-on-dell-mini-9.html") . As the hardware of the mini 10v is practically the same, I suppose this works for you too.

I had read this some days ago, and i tried this but dont work :S

Thanks

---

### Post by chubbypoulet on 2009-06-20
Hello!  I also own a Mini 10v that came with Dell's 8.04 Ubuntu.  I installed the UNR 9.04 and everything worked okay except for the microphone.  Everytime I go into the settings, I see that the microphone icon is crossed out.  Even though I unclick the icon to activate it and save it, but when I open it again, it is automatically crossed out.  Can anybody help me with this issue?  Thanks you in advance.

---

### Post by superm1 on 2009-06-20
> **chubbypoulet said:**
> Hello!  I also own a Mini 10v that came with Dell's 8.04 Ubuntu.  I installed the UNR 9.04 and everything worked okay except for the microphone.  Everytime I go into the settings, I see that the microphone icon is crossed out.  Even though I unclick the icon to activate it and save it, but when I open it again, it is automatically crossed out.  Can anybody help me with this issue?  Thanks you in advance.
Go back to 8.04.  It's patched to support the mic, but the patch that made it upstream appears to have been broke somehow (even on later ALSA builds)

---

### Post by andersja on 2009-06-29
Consider filing a new bug on Launchpad for the devs to have a look at? (if, as reported, sound works in Hardy but not Janunty, be sure to mention it's a regression...)

[https://bugs.edge.launchpad.net/ubuntu/+source/alsa-utils/+filebug](https://bugs.edge.launchpad.net/ubuntu/+source/alsa-utils/+filebug)

---

