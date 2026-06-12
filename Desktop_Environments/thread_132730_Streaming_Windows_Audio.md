---
title: "Streaming Windows Audio"
date: 2006-02-18
forum: Desktop Environments
---

### Post by OneSeventeen on 2006-02-18
My church has streaming windows video, and runs a radio station that streams windows audio.  (I've talked with their web team, and for some reason they refuse to switch to streaming mp3s, which cost the exact same using the service they subscribe to)

Anyway, all rants aside, here's the error message I get:
Totem could not play 'http://65.19.134.2/m88-64 '.
The connection to this server was refused.

From the "listen now" "broadband" portion of [m88.org](m88.org)

What's weird, is totem plays everything else just fine, including the videos from the "services" portion of [calvaryabq.org](calvaryabq.org)

I'm still working on getting them to switch to different streaming formats, but in the mean time, is there any easy way to stream this audio?  (keeping in mind streaming other windows media, including audio, on the church's site)

Are they requiring windows media player or something?  Is this a user-agent issue that the music hosting service is causing?

---

### Post by Vogateer on 2006-02-18
Well it can be played from the console.  Pull up a terminal and type in the following:

mplayer -nocache [http://65.19.134.2/m88-64](http://65.19.134.2/m88-64)

If you have all the win32 codecs on your machine, and you'll have to search for that on the wiki if you haven't installed the necessary codecs for this, mp3, and other non-free codecs.  Not a great solution, I know, but I think the problem is with the website.  Search for CNN Video problems on google, and you might find that something similar is happening on this web page, too.

---

### Post by OneSeventeen on 2006-02-21
Weird, I just tried to open it in VLC, and it worked perfectly.  Is there a way to set VLC as the default media player in firefox?

If so, will that mess up the ability to view/control video/audio from other pages?  (such as the aforementioned services page)

---

### Post by mustang on 2006-02-21
Yup,

[https://addons.mozilla.org/extensions/moreinfo.php?application=firefox&numpg=10&id=446](https://addons.mozilla.org/extensions/moreinfo.php?application=firefox&numpg=10&id=446)

---

