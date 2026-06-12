---
title: "Classic Id Software games?"
date: 2010-05-17
forum: Gaming &amp; Leisure
---

### Post by Silikone on 2010-05-17
I'm curious to try out some of the old games from Id Software on Ubuntu, but I haven't got one to work yet.
 
With Doom, I get a message that tells me it can't load the libraries.
With Quake, it reports that no such file or directory exists when I use ./quake.x11. The file is there, and I "cat quake.x11" just fine.
With Quake 2, I can load it with the softx renderer, but the screen is stretched and displays weird colors (same thing in Quakeworld). The other software renderer requires SVGAlib which I downloaded, but it puts me in a terminal after launching it. I haven't tried the GL modes yet.

---

### Post by dearingj on 2010-05-17
How did you install Doom? I know there is a version of it in Ubuntu's repositories which works on my computers. The relevant packages are prboom (an enhanced Doom engine) and freedoom (a collection of maps for prboom).

Sorry I can't help more than that.

---

### Post by ELD on 2010-05-17
Where did you get the games from and how did you install them? Their engines are open source nowadays and can be found in many places but only a few will be up-to-date enough to work properly.

---

### Post by Rustybolts on 2010-05-17
I use Prboom for Doom / Freedoom
Yamagi for Quake 2
Darkplaces for Quake 1
Eduke for Duke3d

You could always use Dosbox

---

### Post by Silikone on 2010-05-17
I used official engines from ftp.idsoftware.com. I might use a sourceport, but I prefer using vanilla stuff.
I tried prboom, but it quits after some seconds with this message.

```
I_SignalHandler: Exiting on signal: signal 8
```

---

### Post by dearingj on 2010-05-18
> **Silikone said:**
> I used official engines from ftp.idsoftware.com. I might use a sourceport, but I prefer using vanilla stuff.
I tried prboom, but it quits after some seconds with this message.

```
I_SignalHandler: Exiting on signal: signal 8
```

Looks to me like you're being affected by [this bug]("https://bugs.launchpad.net/ubuntu/+source/prboom/+bug/375498").

---

### Post by formaldehyde_spoon on 2010-05-18
> **Silikone said:**
> I'm curious to try out some of the old games from Id Software on Ubuntu, but I haven't got one to work yet.
 
With Doom, I get a message that tells me it can't load the libraries.
With Quake, it reports that no such file or directory exists when I use ./quake.x11. The file is there, and I &quot;cat quake.x11&quot; just fine.
With Quake 2, I can load it with the softx renderer, but the screen is stretched and displays weird colors (same thing in Quakeworld). The other software renderer requires SVGAlib which I downloaded, but it puts me in a terminal after launching it. I haven't tried the GL modes yet.

Doom runs very nicely through DosBox, which is in the repos.

---

### Post by Silikone on 2010-05-18
What about the Quake games? What could be causing X quake to stretch, and what version of SVGAlib is needed?

---

