---
title: "mozilla-mplayer doesnt show video"
date: 2005-10-13
forum: Desktop Environments
---

### Post by mangar on 2005-10-13
after kicking myself in the head, trying to use mozplugger,
(the damn thing wouldn't show several formats, and I didn't find out
how to change the default media-engine to something that isn't totem)

using mozilla-mplayer:
all seems to be working, but when using this site:
[http://fredrik.hubbe.net/plugger/test.html](http://fredrik.hubbe.net/plugger/test.html)

video doesn't show, but the sound is playing.
when clicking on the "show-in-full-frame", the movie plays alright,
but I can't see some of apple's product movies, like the ones in 
new iMac thingies and stuff (err... frustration make the language go brrgmph)

how to make embedded web-media to work?

thanks in advance!

(breezy, alsa not working with my soundcard, w32codecs installed, 
totem-xine (totem-gstreamer can't fast forward, fglrx, pentium-m,
did I forget anything? )

---

### Post by Dec on 2005-10-13
Same Here.. I think totem is the one trying to open the media file in firefox.

---

### Post by mangar on 2005-10-13
just tested, and it works fine using mozilla.
it's not a solution, just a workaround

---

### Post by kerinin on 2005-10-13
i removed all the totem firefox extensions and that fixed most of my problems.  totem kept trying to open media and failing, when mplayer would do it just fine.  

i wish that you were given a choice somewhere as to which plugin to use for each file type in firefox.

---

### Post by mokeyjoe on 2005-10-13
There is a plugin for Firefox which allows you to select any player you have for each media type. I found it when MPlayer wouldn't run embedded WMV files. Now I use Xine and its fine. It does run them in a new Window rather than embedded but I actually prefer that.

---

### Post by mangar on 2005-10-13
how it is called? 
mimetype at the extensions page in mozilla shows 0 results

---

### Post by thechitowncubs on 2005-10-13
[QUOTE=mangar]how it is called? 
mimetype at the extensions page in mozilla shows 0 results[/QUOTE]
MediaPlayerConnectivity

How did you guys get mozilla-mplayer to play in firefox?
I can't for the life of me.

---

### Post by ions on 2005-10-13
I'm getting sound but no video from streaming vid in my browser as well.

---

### Post by mangar on 2005-10-14
I've used "apt-get remove --purge" to remove firefox and
mozplugger, than manually deleted the .mozilla directory and 
/usr/lib/mozilla-firefox
than reinstalled.
than it worked

---

### Post by mangar on 2005-10-14
Where is the Mplayerconnectivity plugin?
i've run a google search, and all i found was this thread
[http://forum.ubuntu-fr.org/viewtopic.php?pid=57378](http://forum.ubuntu-fr.org/viewtopic.php?pid=57378)

which onlu mentions it.

also searching the extension section in firefox web site yielded nothing

thanks in advance!

---

