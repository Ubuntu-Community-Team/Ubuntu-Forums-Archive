---
title: "adding to 'open with' list"
date: 2014-10-03
forum: Desktop Environments
---

### Post by mandarke on 2014-10-03
how do i go about changing the default application from 'videos' to 'mplayer'?

it does not appear in the 'other applications' list and there isn't an obvious way to add the command like in previous versions or alternative file managers.

[IMG]http://i.imgur.com/2Gstmdg.png[/IMG]

---

### Post by fly-by-night on 2014-10-04
I'll take a guess as I have Xubuntu.  

Edit: Nevermind. My suggestion lead to your screenshot. Sorry.

Edit2: Is there no "other" at the end of the Other applications list?

---

### Post by deadflowr on 2014-10-04
I would create a launcher
[https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)

and I believe if you add  %U to the Exec line like,  mplayer %U
it will add it to the open with options.

---

### Post by CantankRus on 2014-10-04
Another easy solution would be to install **smplayer** ....
> **Qt4 Mplayer front-end**, with basic features like playing videos, DVDs, and
VCDs to more advanced features like support for MPlayer filters and more.
One of the most interesting features of SMPlayer: it remembers the
settings of all files you play. So you start to watch a movie but you have
to leave... don't worry, when you open that movie again it will resume at
the same point you left it, and with the same settings: audio track,
subtitles, volume...

---

