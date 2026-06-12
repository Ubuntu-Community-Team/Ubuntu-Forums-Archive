---
title: "Listen To Music From CD's!!"
date: 2009-04-09
forum: General Help
---

### Post by woodbj on 2009-04-09
Hello all, I just installed kubuntu 9.04 and have had the same problem I've had with every other KDE 4.2 distro I've used, audio CD's won't mount but data CD's even DVD movies will, I think they worked for me in KDE 4.1, I'm certain they worked in 3.x.. Does anyone know what the problem is.

---

### Post by askreet on 2009-04-09
It would be helpful if you provide some additional information:
- What happens when you try to play Audio CDs?  (ex.  It appears to be playing, but there is no sound,  I get an error "xyz", The audio is distorted.)
- What media player(s) are you using?

Also,
Try running something like "mplayer" from the command line and see if there is any unusual output.

HTH,
askreet

---

### Post by andrew.46 on 2009-04-09
Hi,

As askreet suggested you could try MPlayer from the commandline:

```
mplayer cdda:// -cache 2048
```

Andrew

---

### Post by woodbj on 2009-04-09
It doesn't matter now it is fixed with KDE 4.2.2

How do I put [SOLVED] on the title

---

### Post by bertolo on 2009-04-09
why bother ?
install amarok.

---

### Post by travhard on 2009-09-26
Andrew -
Your advice helped me discover why my CD's skip, or pause, when I play them using MPlayer or Rhythmbox. The command shows the percentage of buffering while playing, which dropped to zero about once a minute and caused a skip. When I used a cache of 4096 the buffering was adequate, never dropping below 30%

Which suggests this question: Can someone tell me how to add the switch "-cache 4096" to the (unknown) command that I use to open Rhythmbox in the graphical interface under Applications/Sound and Video/Rhythmbox Music Player?

> **andrew.46 said:**
> Hi,

As askreet suggested you could try MPlayer from the commandline:

```
mplayer cdda:// -cache 2048
```Andrew

---

### Post by FunkyRes on 2009-09-26
> **woodbj said:**
> Hello all, I just installed kubuntu 9.04 and have had the same problem I've had with every other KDE 4.2 distro I've used, audio CD's won't mount but data CD's even DVD movies will, I think they worked for me in KDE 4.1, I'm certain they worked in 3.x.. Does anyone know what the problem is.

Audio CD's do not have a filesystem.
They are raw PCM data with a cue list for where certain files stop and start.

Use a multimedia application to play them.

You probably can set a setting to have your audio player auto-start.

Some audio-CDs are actually multi-session with audio + data, the data portion on those disks do have a filesystem and should mount.

GNOME (and MacOS) will mount audio CDs but they emulate a filesystem bases on the cue sheet. I'm guessing either KDE doesn't or your install is not configured to.

---

### Post by StuartN on 2009-09-26
> **travhard said:**
> Can someone tell me how to add the switch "-cache 4096" to the (unknown) command that I use to open Rhythmbox

Incidentally, the commands that a menu item runs can be seen in System Preferences->Main Menu by clicking the properties. The command is rhthymbox, but man rhythmbox shows that there is no user-control of the buffer (unlike VLC or mplayer).

You can set the ALSA sound settings, including the buffer size, through an extremely complicated script file at ~/.asoundrc, for which there is detailed documentation at [http://www.alsa-project.org/main/index.php/Asoundrc](http://www.alsa-project.org/main/index.php/Asoundrc)

There is probably another player that does have more user options that work better for you. I use Gnomeplayer, a GUI front-end to mplayer, that has a cache setting.

---

### Post by travhard on 2009-09-27
> **StuartN said:**
> Incidentally, the commands that a menu item runs can be seen in System Preferences->Main Menu by clicking the properties. The command is rhthymbox, but man rhythmbox shows that there is no user-control of the buffer (unlike VLC or mplayer).
[snipped]

There is probably another player that does have more user options that work better for you. I use Gnomeplayer, a GUI front-end to mplayer, that has a cache setting.

StuartN: The first suggestion is helpful, thank you. I was able to append to the command line of mplayer.

I tried Gnomeplayer, but when hovering over the cache window, I see the message that the cache is for playing media from a network. It does not help prevent the pauses in CD  playbacks. 

Thanks.

---

### Post by StuartN on 2009-09-27
> **travhard said:**
> I tried Gnomeplayer, but when hovering over the cache window, I see the message that the cache is for playing media from a network.

Sorry, my mistake. The great thing is, though, that the advanced tab of the Gnomeplayer preferences has a field for "extra options to mplayer" where you can put **-cache 4096**, or any other mplayer command line options.

---

