---
title: "amaroK problems"
date: 2006-01-12
forum: General Help
---

### Post by SoarAF on 2006-01-12
Ok,
I have kubuntu installed, the newest and for some reason amaroK will not recognize the track info at all, just the name...I would really like it to recognize the album names so that i can organize it all with that...also, for some reason i cant get the newest version of amaroK, it says that 1.3.1 is the newest and wont upgrade...i think it has something to do with MySql but i have no idea how to configure that and cant find anything online about it...also, my mp3s are being run from my windows partition and were all converted to mp3...but i did it before and amaroK recognized the few that i did convert the same way, its just not doing it now...any help?

---

### Post by defuseme2k on 2006-01-13
You need to enable more respositories in adept to get the latest version of amaroK.  You should also get the amarok xine plugin.  Seems to take a reboot to get amarok to load up the new plugin... I dunno it did for me anyway.

After that you can switch to the xine engine in amarok to play your mp3 files as it then can decode them *rolls eyes* and it can play streams as well then.  gstreamer just told me it couldn't play mp3's and trying to stream audio with it didn't work either.

GL.

---

### Post by Brando569 on 2006-01-13
gstreamer is a major PITA, ever since i disabled hotplug alsa or something doesnt load but my sound still works but kaffeine/amarok wont play files cuz it says the device doesnt exist :rolleyes: ive been using totem for a lil while

edit: gstreamer is the PITA amarok still is awesome, changed to xine and everything works fine :)

---

