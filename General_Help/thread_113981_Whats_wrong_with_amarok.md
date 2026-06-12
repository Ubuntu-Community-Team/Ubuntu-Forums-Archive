---
title: "Whats wrong with amarok?"
date: 2006-01-07
forum: General Help
---

### Post by bencrouse on 2006-01-07
Hello,
I'm new to kubuntu, but not to ubuntu.  I'm trying to play mp3s.  I installed the gstreamer0.8 and akode-mpeg according to the kubuntu faq, but now whenever i click a song to play, it says "playing" but there is no sound, and it just stays at 0:04.  if i try to move to a different time, no matter what the file, it goes back to 4sec, and says playing.  the pop up thing shows as well when i click a track, but nothing plays.
whats going on here?
Thanks
ben

---

### Post by awakatanka on 2006-01-07
[QUOTE=bencrouse]Hello,
I'm new to kubuntu, but not to ubuntu.  I'm trying to play mp3s.  I installed the gstreamer0.8 and akode-mpeg according to the kubuntu faq, but now whenever i click a song to play, it says "playing" but there is no sound, and it just stays at 0:04.  if i try to move to a different time, no matter what the file, it goes back to 4sec, and says playing.  the pop up thing shows as well when i click a track, but nothing plays.
whats going on here?
Thanks
ben[/QUOTE]
Did you install the codecs? If not configure youre sources.list a how to and some extra lines can be found on : [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

You need to install multimedia packets.

---

### Post by claydoh on 2006-01-07
Also try switching from the gstreamer engine to either arts or xine.

---

### Post by carl13 on 2006-01-07
I use the oss engine and it works fine.

---

### Post by ace2005 on 2006-01-07
Install amarok-arts

Go into kcontrol and pick Alsa as the output hardware, thats the one that works the best for me but you might want to try some of the others. Make sure that "Auto-Suspend if idle after" is set to something like 1 second, so that if amarok stops playing other apps can use the sound system

Go into amarok and pick arts as the engine and that should do it

If not install amarok-xine, go into xine and pick arts as audio output, then go into amarok and pick xine as the engine and it'll work, You might need to have the win32 codecs installed.

IF you use arts as sound output in xine or any other video apps, you may find that the audio is out of sync and that there is a delay, so using alsa directly in video apps is the best thing to do, but its fine for just audio like playing MP3s

---

### Post by Brando569 on 2006-01-07
amarok is a pain in the @$$ thats why, ive had sooo many problems with it but i still stick with it.

---

