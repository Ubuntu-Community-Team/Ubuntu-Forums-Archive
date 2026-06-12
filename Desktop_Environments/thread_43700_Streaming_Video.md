---
title: "Streaming Video"
date: 2005-06-22
forum: Desktop Environments
---

### Post by wwwolf on 2005-06-22
I can't seem to figure out how to play this file:

mms://video.pbs.org/general/windows/media4/frontline/2315/windows/ch1_hi.wmv

I have tried the "play URL" option in gmplayer since mplayer has the codecs needed to watch wmv files:

error message: [COLOR=Red] Unable to open URL mms://video.pbs.org/general/windows/media4/frontline/2315/windows/ch1_hi.wmv
[/COLOR]

, I have also tried Kaffeine which is also configured to play wmv files:

error message: 2 windows pop up,[COLOR=Red] Kaffeine error: The connection was refused. Check the host name. (), 
[/COLOR]
and a xine error window:[COLOR=Red] xine: cannot find input plugin for MRL [mms://video.pbs.org/general/windows/media4/frontline/2315/windows/ch1_hi.wmv]
xine: input plugin cannot open MRL [mms://video.pbs.org/general/windows/media4/frontline/2315/windows/ch1_hi.wmv]
io_helper: Connection Refused
xine: found input plugin : mms streaming input plugin
[/COLOR]
. I have tried downloading it with Konquorer:

error message: [COLOR=Red]Could not start process Unable to create io-slave: Klauncher said: unknown protocol 'mms'.
[/COLOR]

 and also with wget.

error message:[COLOR=Red] mms://video.pbs.org/general/windows/media4/frontline/2315/windows/ch1_hi.wmv: Unsupported scheme.
[/COLOR]
any help on any method would be appreciated. Thanx,

---

### Post by StacyWebb on 2005-06-22
you need to get the win32 codecs. This will sove your issues. Look [here](http://ubuntuguide.org/)  Should have all your answers.

---

### Post by wwwolf on 2005-06-23
[QUOTE=StacyWebb]you need to get the win32 codecs. This will sove your issues. Look [here](http://ubuntuguide.org/)  Should have all your answers.[/QUOTE]

Thanx for the reply but I have already installed the win32 codecs long ago or I would not be able to play wmv files. My codecs are working properly.

Any other ideas?

---

