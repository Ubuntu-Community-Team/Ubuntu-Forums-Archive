---
title: "[SOLVED] Amarok playback skips briefly"
date: 2008-01-31
forum: Desktop Environments
---

### Post by llobster on 2008-01-31
I'm experiencing some brief pauses during playback in amarok that seem random and are very annoying. it's similar to a cd skipping

I haven't found a way to purposefully get it to skip, it just seems to happen at random. It will occur during any level of CPU usage, with or without firefox open, with or without other programs using sound. I haven't noticed a skip in other programs either (ie: VLC).

I have already undone the constant monitoring of my collection and I set it up for MySQL, and Amarok itself doesn't really ever act sluggish, it's just the playback that seems to skip at random (maybe five or six times per song).

I tried forcing the 48000 sampling rate too, and it didn't change, but confusingly when i reopened xine-config those lines had disappeared. i didn't bother trying again, because since it's random timing i don't think it can be a sampling issue.

i have a soundmax onboard soundcard (ASUS p4pe mobo) using SPDIF
my music is stored on a sata1 NTFS drive (video run from the same drive doesn't seem to hiccup in VLC)
i tried switching to passthrough too and nothing changed

any ideas?

edit: i was wrong, sound from any program (vlc, exaile, rhythmbox) and from any drive skips randomly...i guess it must be a driver issue

solved: ends up my receiver, which was set to auto detect spdif or analog, was randomly dropping the digital signal for analog for a split second. forcing it digital seems to have solved it. i don't know why it's doing it, doesn't happen if i boot to windows or if i plug my mac in, but thankfully it's solved

---

### Post by mpstump on 2008-02-16
Could you elaborate on this? I have the same problem. It seems like my hardware is detecting something, and the CPU fan increases intensity, and then my music skips. Doesn't happen with video, but happens consistently with any music/player app.

---

### Post by 4KvRMU7Nnv on 2008-02-16
happens to me too.  Only on Amarok.  Also, I am not noticing any CPU increase or anything, but I haven't checked either.  It seems to be random.

---

### Post by starryeyedboy on 2008-02-22
I never had this issue - till today, when my rhythmbox started crashing, n i tried using several other music players. Once things started working again, i noticed that music playback skips. The skips occur in the exact same position, for a certain song, but its different, for different songs. I haven't tested whether its the same for other apps like VLC - 

could you explain, how did u force the receiver to be digital only?

i've been googling n searching all night, but i really can't find anything on it..

thanks!

---

