---
title: "last.fm"
date: 2006-09-11
forum: Desktop Environments
---

### Post by u534_n4m3 on 2006-09-11
i heard that last.fm is a pretty good music streaming service.  i just have a couple of quick questions about it.

is last.fm free?  are all songs available for streaming or are only selected (popular ones) available?

should i install last.fm or last.exit?  how do you install it on a fresh new installation of ubuntu (fully upgraded using the synaptics download manager)?


thanks

---

### Post by someguyouknow on 2006-09-11
I use Amarok for last.fm
its free. i dont think you can pick the songs you want. you have stations of music similar to things you like.

---

### Post by u534_n4m3 on 2006-09-11
> **someguyouknow said:**
> I use Amarok for last.fm
its free. i dont think you can pick the songs you want. you have stations of music similar to things you like.

is last.fm kinda like launchcasts premade stations?

isn't amarok for kde?  i'm currently using gnome.  i currently have rythmbox.  anyway to stream last.fm on a webbrowser?  i have firefox

---

### Post by someguyouknow on 2006-09-11
check and see if rythmbox supports it. i think it does but i am not sure.
yes, its premade stations as far as i can tell.  not sure about webbrowsers.

there is custom radio too though.

---

### Post by u534_n4m3 on 2006-09-11
> **someguyouknow said:**
> check and see if rythmbox supports it. i think it does but i am not sure.
yes, its premade stations as far as i can tell.  not sure about webbrowsers.

there is custom radio too though.

what's the software for (the one downloadable from the last.fm site)?

how do i check if rythbox works with last.fm?


sorry for all the newb questions.  i'm just starting with linux and i really really miss the launchcast service for windows.

---

### Post by someguyouknow on 2006-09-11
same thing i guess. never needed it. Amarok is all i use/need.
even though its KDE, you should check out Amarok. Its great.

---

### Post by someguyouknow on 2006-09-11
Rhythmbox does support last.fm but i dont know how to do it. I dont have it installed

---

### Post by u534_n4m3 on 2006-09-11
> **someguyouknow said:**
> same thing i guess. never needed it. Amarok is all i use/need.
even though its KDE, you should check out Amarok. Its great.

does amarok work in gnome?  if so, how do i install it?

---

### Post by someguyouknow on 2006-09-11
yea it works. just do sudo aptitude install amarok. or use synaptic.

---

### Post by szf on 2006-09-11
Amarok will also install all the KDE libs! Acknowledge that fact before you do so...

By the way last-exit [[ubuntu package]("http://www.burtonini.com/blog//computers/last-exit-2006-07-10-10-12?showcomments=yes")] is a last.fm player for Gnome.

---

### Post by someguyouknow on 2006-09-11
> **szf said:**
> Amarok will also install all the KDE libs! Acknowledge that fact before you do so...

By the way last-exit [[ubuntu package]("http://www.burtonini.com/blog//computers/last-exit-2006-07-10-10-12?showcomments=yes")] is a last.fm player for Gnome.

i think its worth it lol.
but thats just me :p

---

### Post by u534_n4m3 on 2006-09-11
> **szf said:**
> Amarok will also install all the KDE libs! Acknowledge that fact before you do so...

By the way last-exit [[ubuntu package]("http://www.burtonini.com/blog//computers/last-exit-2006-07-10-10-12?showcomments=yes")] is a last.fm player for Gnome.

noob question:  how do i install last-exit?  i downloaded the tar.gz file on my desktop and extracted it.  what's next?

i tried "./configure" in the terminal and it gave me this error:  "checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool"

what do i need to install?

---

### Post by szf on 2006-09-11
Yeah, KDE (and Trolltech) have shown themselves to be a compelling Linux Desktop. Myself, I started with Gnome - and with the exception of an on-again/off-again flirtation with K3B, I find that having both desktop platforms installed muddles the menus.

---

### Post by szf on 2006-09-11
> **u534_n4m3 said:**
> noob question:  how do i install last-exit?  i downloaded the tar.gz file on my desktop and extracted it.  what's next?

Ross Burton packaged the .deb file in his [repository]("http://burtonini.com/debian/"). Navigate to Dapper and then to file last-exit_2.0-1_i386.deb. Download that file.

Then:
[FONT="Courier New"]$ sudo dpkg -i last-exit_2.0-1_i386.deb[/FONT]

While the file is a true debian package - this is not the preferred mechanism to get packages. Given Ross Burton's (considerable!) activity in the community - I believe that it's safe to install from there.

---

### Post by someguyouknow on 2006-09-11
> **szf said:**
> Yeah, KDE (and Trolltech) have shown themselves to be a compelling Linux Desktop. Myself, I started with Gnome - and with the exception of an on-again/off-again flirtation with K3B, I find that having both desktop platforms installed muddles the menus.

ah...
I started with KDE and will probably stay. though i do have some gnome apps.

---

### Post by u534_n4m3 on 2006-09-11
> **szf said:**
> Ross Burton packaged the .deb file in his [repository]("http://burtonini.com/debian/"). Navigate to Dapper and then to file last-exit_2.0-1_i386.deb. Download that file.

Then:
[FONT="Courier New"]$ sudo dpkg -i last-exit_2.0-1_i386.deb[/FONT]

While the file is a true debian package - this is not the preferred mechanism to get packages. Given Ross Burton's (considerable!) activity in the community - I believe that it's safe to install from there.

terminal gave me this error about mono or something.  how do i install mono? and where do i get it?

---

### Post by themoebius on 2006-09-12
Amorok and Rythmbox, etc, as far as I know only submit your mp3 listening habits to your last.fm account so they can figure out what kind of music you might like and tailor your personal radio station to your tastes. I think you need the last.fm client or perhaps some 3rd party client to actually listen to their streams. Their linux client is pretty good though.

---

### Post by someguyouknow on 2006-09-12
You can listen to streams with Amarok.

---

### Post by szf on 2006-09-12
The October 2006 issue of Linux Journal 'Cooking With Linux' column covers media players, pandora, and last.fm usage. I just checked and it appears that linuxjournal now puts things behind the subscriber wall :( so YMMV.

Amarok (KDE) and Banshee (Gnome with Mono) report listening habits to last.fm, when configured. The statically linked KDE-based last.fm player as well as last-exit (GTK2) will play music streams from last.fm.

Oh just looked at the article: someguyouknow is correct - Amarok can tune into last.fm (it says Neighbour Radio). There are also reporting plugins for XMMS, Noatun, and others.

---

### Post by szf on 2006-09-12
> **u534_n4m3 said:**
> terminal gave me this error about mono or something.  how do i install mono? and where do i get it?

Sorry for missing the chance to respond in good time. It may sound like a dumb-*** suggestion, but if you're missing Mono (i.e. dot-NET for Linux) if you grab a Ubuntu package thru Synaptic (Add Programs) that relies on Mono - it will install it as a dependency.

Applications in the Ubuntu repos that will require Mono: Beagle (Desktop Search), Banshee (Music Player), F-Spot (Photo Management).

---

