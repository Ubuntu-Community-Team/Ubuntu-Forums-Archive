---
title: "couldnt play .wmx on webpage and .mov"
date: 2005-05-27
forum: Desktop Environments
---

### Post by tommi on 2005-05-27
Hiho. My problem, i cant watch the trailer on : [http://www.fox.de/nightwatch/trailer.html](http://www.fox.de/nightwatch/trailer.html) 

or

[http://www.freenet.de/freenet/webvideos/kino_trailer/](http://www.freenet.de/freenet/webvideos/kino_trailer/)

I Use Konquerer and kaffeine with xine + w32codecs from nerim (testing). I could watch the trailers from [http://www.apple.com/trailers](http://www.apple.com/trailers) but i have some probs with .mov (couldnt play). 

then i heard i should use mplayer with mplayer-mozilla (works with konquerer too). but mplayer-mozilla will install xmms, gtk 1.2, gtk 2.0, ,mozilla-firefox and many other packets. thts not good because i doesnt want install all this. mplayer will depend on this , too.

i requestet the new lib-xine (maybe the old 1.0 iss the source of error) as backport. but i dont know.

 could anybody help ? what should i do ? (can i install this without gtk/xmms ?
will the use of gstreamer with all plugins fix this ? hmm its hard to use linux *grins*

---

### Post by ludi on 2005-05-27
[QUOTE=tommi]Hiho. My problem, i cant watch the trailer on : [http://www.fox.de/nightwatch/trailer.html](http://www.fox.de/nightwatch/trailer.html) 

or

[http://www.freenet.de/freenet/webvideos/kino_trailer/](http://www.freenet.de/freenet/webvideos/kino_trailer/)

I Use Konquerer and kaffeine with xine + w32codecs from nerim (testing). I could watch the trailers from [http://www.apple.com/trailers](http://www.apple.com/trailers) but i have some probs with .mov (couldnt play). 

then i heard i should use mplayer with mplayer-mozilla (works with konquerer too). but mplayer-mozilla will install xmms, gtk 1.2, gtk 2.0, ,mozilla-firefox and many other packets. thts not good because i doesnt want install all this. mplayer will depend on this , too.

i requestet the new lib-xine (maybe the old 1.0 iss the source of error) as backport. but i dont know.

 could anybody help ? what should i do ? (can i install this without gtk/xmms ?
will the use of gstreamer with all plugins fix this ? hmm its hard to use linux *grins*[/QUOTE]
 Hi.
Mplayer-plugin don't work in konqueror, so you have to use kmplayer or kaffeine plugin to do that.
Well, I'm watching your trailer in this moment  at konqueror with kmplayer :)
I've tried others programs but just kmplayer worked.
Whatever, avifile-win32-plugin, w32codecs, libxine or mplayer should play any windows formats without any problem. Now you have to choose what embedded player do you want. Mplayer-plugin works just fine for Firefox and kmplayer works great in Konqueror.
There is no kmplayer binary package to ubuntu (or Debian), so you have to compile it.

---

