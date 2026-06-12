---
title: "Sound Blaster Audigy 2"
date: 2005-12-06
forum: General Help
---

### Post by soup440 on 2005-12-06
How do I install the drivers for this soundcard? I could'nt find anything on the internet, thanks.

---

### Post by amohanty on 2005-12-06
It should be automatically detected. I have the Audigy 2ZS on an Asus K8N and it worked fine from the get go with 5.1

I woudl suggest that you try the following:

In alsamixer:
enable/unmute everything except:
SPDIF output (if you are using analog speakers)
Eveything that says OPtical 

I will post a screen shot when I get home.

HTH

---

### Post by soup440 on 2005-12-06
The thing is that Linux detects the onboard Hi-Def audio on my intel motherboard, so I need to tell it to use my sound card and not my onboard audio
Thanks!

---

### Post by Gray. on 2005-12-06
Try going to
System > Preferences > Sound
and try changing your default sound card in the drop-down list there.
You could also try disabling the onboard audio in the BIOS? This would make Ubuntu only use your Audigy2.

---

### Post by amohanty on 2005-12-07
Sorry I did not mention this earlier, I have disabled my onboard BIOS like Gray suggested.

---

### Post by soup440 on 2005-12-07
Ok I got the sound going into my soundcard, can I change the bass and treble levels as well as use EAX? Im a bit of an audiophile so this really matters to me, or is this in "alsamixer?"

---

### Post by amohanty on 2005-12-07
Heres what I have found I can control. I couldnt find a tool to actually use EAX so I couldnt say about that.

[ATTACH]4220[/ATTACH]

HTH

---

