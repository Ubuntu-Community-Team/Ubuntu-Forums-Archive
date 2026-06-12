---
title: "Crackling sound in OpenArena."
date: 2010-01-09
forum: Gaming &amp; Leisure
---

### Post by bhishan on 2010-01-09
I have this crackling sound problem in OpenArena. I use Karmic 64bit, filesystem is ext4. It is really annoying. The sound sometimes works but most of the time it is crackling. Anyone knows a solution?

---

### Post by rand()m on 2010-01-09
Can I suggest trying to run the game from a Kubuntu LiveCD/USB and see if the same thing happens?

If it doesn't then chances are it's PulseAudio related.

---

### Post by bhishan on 2010-01-10
@Rand()m: Thanks for the suggestion.

Anyone got a easier solution?

---

### Post by del_diablo on 2010-01-10
sudo apt-get remove pulseaudio

---

### Post by bhishan on 2010-01-10
> **del_diablo said:**
> sudo apt-get remove pulseaudio

Do i have to replace pulseaudio with anything else or just removing it will work?

---

### Post by Twitch6000 on 2010-01-11
> **bhishan said:**
> Do i have to replace pulseaudio with anything else or just removing it will work?

Sorry but do not follow what the above person said.

Due to how ubuntu has made pulseaudio so needed removing it will kill your system.

However what you can do is install esound and then to go sound devices and make it use esound instead of pulseaudio.

This should fix the problem.

---

### Post by bhishan on 2010-01-11
> **Twitch6000 said:**
> Sorry but do not follow what the above person said.

Due to how ubuntu has made pulseaudio so needed removing it will kill your system.

However what you can do is install esound and then to go sound devices and make it use esound instead of pulseaudio.

This should fix the problem.

Sorry, where is sound devices?

---

### Post by Sockerdrickan on 2010-01-12
> **bhishan said:**
> I have this crackling sound problem in OpenArena. I use Karmic 64bit, filesystem is ext4. It is really annoying. The sound sometimes works but most of the time it is crackling. Anyone knows a solution?
Trust me, your filesystem is not relevant to audio issues xD

It is possible that this is a problem with OpenAL, use the latest OpenAL Soft release and it should work.

---

### Post by KIAaze on 2010-03-28
I had the same problem and managed to fix it by removing timidity:
```
sudo apt-get remove timidity timidity-daemon
```

Check this for more troubleshooting tips:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)
(Making timidity use esound did not work for me. I got some error messages when restarting timidity.)

Remaining sound problems:
-no sound in liquidwar
-crackling sounds in tiny and big: [http://www.tinyandbig.com/](http://www.tinyandbig.com/) (still in development, so might only be a game-specific issue)

---

### Post by bhishan on 2010-04-03
I had not played the game for a couple of months due to the sound issue. Yesterday I gave it a try and magically there was no sound problem. I have no idea how it got fixed.

---

### Post by Sockerdrickan on 2010-04-04
> **bhishan said:**
> I had not played the game for a couple of months due to the sound issue. Yesterday I gave it a try and magically there was no sound problem. I have no idea how it got fixed.
Perhaps you updated to a new Ubuntu version? And got OpenAL Soft

---

### Post by bhishan on 2010-04-05
> **Sockerdrickan said:**
> Perhaps you updated to a new Ubuntu version? And got OpenAL Soft

No, it has been Karmic all along. Whatever fixed it, i am happy now :)

---

