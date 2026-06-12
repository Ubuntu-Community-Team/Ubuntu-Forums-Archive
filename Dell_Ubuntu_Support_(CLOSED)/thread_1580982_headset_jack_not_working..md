---
title: "headset jack not working."
date: 2010-09-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by c2tarun on 2010-09-24
hi friends
i am using dell inspiron 1410n and ubuntu 10.04 lucid
my headset jack is not working. it was working fine with windows 7
can anyone please help.
thanx

---

### Post by ptptaylor on 2010-09-24
In the audio control panel in the top right of your screen, go to sound preferences, the output tab. Choose the connector as analog headphones (or whatever the right one is).
I find it quite nice this feature although it doesn't seem like it should be. It means that your laptop doesn't make noise accidentally if the headphones aren't plugged in.

---

### Post by c2tarun on 2010-09-24
not working.
i opened alsamixer in terminal and there is no sound control for headphone.
please reply

---

### Post by c2tarun on 2010-10-03
bump

---

### Post by c2tarun on 2010-10-04
help

---

### Post by c2tarun on 2010-10-06
bump

---

### Post by ptptaylor on 2010-10-06
What sound card are you using there?
Press f6 in the alsamixer

---

### Post by KegHead on 2010-10-06
Hi!

Goto preferences..sound...uncheck "mute"

Worked for me.

KegHead

---

### Post by c2tarun on 2010-10-06
> **ptptaylor said:**
> What sound card are you using there?
Press f6 in the alsamixer


i think default is selected
and other two options were
0 HDA Intel
1 HD-Audio Generic

---

### Post by c2tarun on 2010-10-08
bump

---

### Post by bobmartens on 2010-10-19
> **c2tarun said:**
> hi friends
i am using dell inspiron 1410n and ubuntu 10.04 lucid
my headset jack is not working. it was working fine with windows 7
can anyone please help.
thanx
I'm not really sure if the alsamixer has tge option stereo duplex out, this option should fix your problem, let me know if it did or did not, ok?

---

### Post by c2tarun on 2010-10-19
> **bobmartens said:**
> I'm not really sure if the alsamixer has tge option stereo duplex out, this option should fix your problem, let me know if it did or did not, ok?


well i m not getting what u want to say.
can you please explain a bit.

---

### Post by bobmartens on 2010-10-19
the stereo duplex output option is all a regular user will ever need. Check all faders in the mixer. They might be muted for example. In the options or preferences there are a lot more faders you can activate. Some of those needed might not yet been chosen. Wav out, movie vol, master out, mic in. Experiment with these, no harm can be done by trying them all. No result? try on... Start doing this using you built-in speakers. if these do the job, your problem is most likely a setting of your external speakersystem. Any useful info in this reply?

---

