---
title: "Remote Desktop Issues"
date: 2009-05-21
forum: General Help
---

### Post by solidsmoke on 2009-05-21
I have an old PC in my room that I'm using as a file server (jaunty). It doesn't have a monitor, or keyboard/mouse etc. so having remote desktop work would be handy. I SSH'd the server from my laptop and opened up vino-preferences to try and enable it, but ended up with this result:

[IMG]http://i4.photobucket.com/albums/y124/solid_smoke/Screenshot-RemoteDesktopPreferences.png[/IMG]

Just from localhost?! It can only accept remote desktop connections from itself? Any suggestions would be great...

I want to be able to do stuff like, leave transmission running on it for downloads, which i COULD do with SSH, but then i'd have to leave a terminal open on my laptop all the time... unless theres a way around that. i could just use that if i cant get remote desktop working.

---

### Post by chriskin on 2009-05-21
remote desktop shows strange things from time to time at my jaunty, but i just unclick and re-click the third option of security, and it usually gets to give me the ip and the name of the computer so that remote can work

---

### Post by solidsmoke on 2009-05-21
> **chriskin said:**
> remote desktop shows strange things from time to time at my jaunty, but i just unclick and re-click the third option of security, and it usually gets to give me the ip and the name of the computer so that remote can work

Just tried that, but it didn't work out. :(

---

### Post by solidsmoke on 2009-05-21
buuuuuuump

---

### Post by geirha on 2009-05-21
It should listen on all interfaces, even though it just says localhost there. Just make sure port 5900 is open, and connect to the vnc server with the IP/hostname you use to ssh in with.

As for transmission, it has a built-in web UI, which you can enable in the preferences. From the web UI you can do most things you can with the regular GUI.

---

