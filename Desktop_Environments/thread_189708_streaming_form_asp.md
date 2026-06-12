---
title: "streaming form asp"
date: 2006-06-05
forum: Desktop Environments
---

### Post by NESFreak on 2006-06-05
i am able to stream windows media embeded tru the totem-xine-plugin but when i try to open it in an external player it gives an error that it does not have the plugin for .asp. Mplayer also isn't able to play it.

i have this problem with several streams this is one of them.
[http://www.garnierstreamingmedia.com/asx/pinkpop-sb.asp]("http://www.garnierstreamingmedia.com/asx/pinkpop-sb.asp")
[orriginal website]("http://3voor12.vpro.nl/3voor12/live/player_video.jsp?programs=11998947&lstreams=12001517")
any sugestions?

---

### Post by NESFreak on 2006-06-05
i found out that it has got something to do with this thing called streamswitch

How do i make totem read these things?

---

### Post by NESFreak on 2006-06-05
LOL when i downlaod the asp and change the p to an x totem does recognise it.
So now how do i make totem automaticaly think that asp is asx?

---

### Post by Snam on 2006-07-16
Hello,

I've got 3 questions about Totem:

Question 1:
I downloaded [http://www.garnierstreamingmedia.com/asx/kinkfm.asp](http://www.garnierstreamingmedia.com/asx/kinkfm.asp). Renamed the asp to asx. But then Totem gives the following error:

Totem could not play 'mmsh://81.23.249.10/kinkfm?MSWMExt=.asf'.

How do I solve this problem?

BTW when I try to play the asp directly, I get the following error:
Totem could not play 'mmsh://81.23.249.10/kinkfm?MSWMExt=.asf'.
No URI handler implemented for "mmsh".

Question 2:
When I try to stream: [http://www.kinkfm.com/streams/kinkfm.m3u](http://www.kinkfm.com/streams/kinkfm.m3u), I get the following error:
Totem could not play 'http://www.garnierstreamingmedia.com/asx/kinkfm.pls'.
Could not determine type of stream.

How do I solve this problem?

Question 3: How do I play QuickTime .mov movies?

Regards,

Snam

---

### Post by NESFreak on 2006-07-16
for .mov you need the win32 codecs

asp is a serverside scripting language just like php. In some cases this script is to generate a .asx playlist, though totem wouldn't recognise it. Changing the file extension from .asp to .asx only works when the file the webserver send is in fact a by asp generated asx file.

---

### Post by lekbe2003 on 2006-12-22
> **NESFreak said:**
> for .mov you need the win32 codecs

asp is a serverside scripting language just like php. In some cases this script is to generate a .asx playlist, though totem wouldn't recognise it. Changing the file extension from .asp to .asx only works when the file the webserver send is in fact a by asp generated asx file.

Hi check this out [https://launchpad.net/distros/ubuntu/+source/gstreamer0.10/+bug/46217](https://launchpad.net/distros/ubuntu/+source/gstreamer0.10/+bug/46217)

good luck

---

