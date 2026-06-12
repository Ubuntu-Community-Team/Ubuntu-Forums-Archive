---
title: "Real video and audio streams in Firefox"
date: 2005-11-03
forum: Desktop Environments
---

### Post by jonny on 2005-11-03
Firefox and Epiphany both default to using gxine for Real audio and video streams, even though I have Real Player 10 installed.  Unfortunately, gXine can’t read Real video so I get an error message.  Other video and audio opens in a neat embedded Totem window (I’m using mozplugger)

Does anyone know how I can get Firefox to to know that Real Player exists?  Even better does anyone know how to get embedded Totem-xine to play these streams?

BBC News has plenty of Real streams for anyone who wants to find out what happens on their system.

---

### Post by manicka on 2005-11-03
How did you install real player?

---

### Post by Hairy_Palms on 2005-11-03
to make xine play realmedia, go to the place that realplayer is installed and go to  the plugins subdirectory then copy the whole lot to /usr/lib/win32 worked for me with the mplayer plugin.

---

### Post by jonny on 2005-11-03
To install realplayer, I downloaded it and ran the installer.  Put the executables in /opt.  Said yes to create system wide symlinks question, and used the default /usr as the location.  It appeared automatically on my applications menu, and I can also access it from the command line.

So far, so good.  But Firefox don' wanna play

---

### Post by shinygerbil on 2005-11-03
Try installing mozplugger - it fixed my Opera *and* my FF :) I'm still not sure about Realplayer though, I've never had to look at any so I don't know...
But if it's there, plugger should pick it up :)

Steve

---

### Post by jonny on 2005-11-03
I'm using mozplugger.  It worked perfectly under Hoary, but I was using mplayer, not Totem as a plugin.

Totem's better because it provides on-screen controls.

---

### Post by shinygerbil on 2005-11-03
I've always had problems with totem - so I uninstalled it. :/ so I can't really help you there..

Steve

---

### Post by bionnaki on 2005-11-03
just change the download action in firefox.
preferences>downloads
find .rm, .rma, .cgi or whatever else you want to
open up in real player.
"change action" and browse to your location
of you real player installation.
point it to "realplay"

---

