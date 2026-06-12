---
title: "Wine Firefox &amp; Multimedia Woes"
date: 2006-09-23
forum: Desktop Environments
---

### Post by Jose Catre-Vandis on 2006-09-23
I have tried, really hard, to get everything to work, but it just won't do it and I know I am close [-o< 

Here is the setup.

We had, one might say, a few too many XP installations in our house, for our consciences, so it was time to do something about it and move over to Ubuntu. For me, not such a problem, for my kids a bit more of a challenge. They are great fans of [www.neopets.com](www.neopets.com), which makes heavy use of Flash, Shockwave and embedded media, none of which come naturally to Ubuntu :razz: 

So the machines were setup with Dapper 6.06.1 and Automatix to take care of much of the requirements and multimedia.

I first tried IES4Linux2.0 but this was buggy and horribly flashy on the eyes. So..

Then installed the Windows version of Firefox under WINE, which consequently allowed the successful installation of Shockwave.
(followed this [thread]("http://www.ubuntuforums.org/showthread.php?t=259237&highlight=shockwave") , and this [howto]("https://help.ubuntu.com/community/Shockwave"))

So far so good, kids could now play the shockwave games using the keyboard and mouse, but they had no sound and Firefox under Wine could not seem to play embedded media. So I had a look at how Firefox natively played sound, appearing to use mplayer plugin, and also how Firefox in Windows worked, by default using Quicktime. Note that sound did work in Firefox under Wine, tested it out on Youtube.

So I tried installing Quicktime 7 [COLOR="Red"]nope[/COLOR], Quicktime Alternative, [COLOR="Red"]nope[/COLOR], Mozilla Activex plugin, [COLOR="Red"]nope[/COLOR], mplayer for Windows and the mplayer plugin extension, [COLOR="Red"]nope[/COLOR], the bgsound extension, [COLOR="Red"]nope[/COLOR], Windows media player classic by itself, [COLOR="Red"]nope[/COLOR].

Have now run out of ideas. for me its seems that the media player, whichever I choose, will be happy to play sound, but I cannot get a plugin to direct the sound file to it. Similarly, not sure why I do not get sound in shockwave games (can't do the alsa-aoss fix here!)

I know its a somewhat convoluted route to acheive neopets nirvana for my kids, but it appears to be the only way. Can anyone give me any pointers of where to go next?

---

### Post by Jose Catre-Vandis on 2006-09-28
A kind of bump:

Tried out PCLINUXOS .93a. Installed wine, Windows Firefox and Shockwave. Get action and sound with shockwave games, so it does work. PCLINUXOS reports it is using an Intel sound driver!

---

### Post by Jose Catre-Vandis on 2006-09-29
OK, a little further ahead. Upgraded wine to 0.9.2.1 and sound now plays in shockwave :-)

Next challenge to get bgsounds working. I installed Quicktime 6.5.1 which nearly works with choppy sound, but I get screen blackouts as well. looking now for an alternative to QT. Doesn't seem to be an mplayer plugin equivalent for windows firefox :-(

---

### Post by Jose Catre-Vandis on 2006-09-29
Am made up, have got the whole of Neopets -flash games and bgsound working, under Linux Firefox!!!

bgsound sound requires the extension from [http://bgmconductor.svist.net/](http://bgmconductor.svist.net/)

Flash 7 plugin (hacked to V9 although not sure if this helps) along with a full install from Automatix of all codecs and plugins.

Then a little trick. When you open a flash game in Neopets, minimise the window, and then maximise it / restore it, and hey presto, your keyboard works and you can play the game.

Its a minor annoyance, would be nice to be able to fix it, but will keep the kids happy for now, and keep them on Ubuntu :D

---

