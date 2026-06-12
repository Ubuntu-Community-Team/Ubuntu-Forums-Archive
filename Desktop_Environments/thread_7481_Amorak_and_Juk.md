---
title: "Amorak and Juk"
date: 2004-12-07
forum: Desktop Environments
---

### Post by adpsimpson on 2004-12-07
Hi, firstly thanks for a great distro. Having used Mandrake for over a year, I was getting fed up with the bugs and just ready to try a Debian-based distro, and just then Ubuntu stepped in... So far I have no complaints. Everything is incredibly stable, well configured etc. Preferring KDE to Gnome, I was amazed at how little hassle it was to install.

However I'm having one problem. I have a large number of mp3s, and have previously used Juk to play them, but it's not doing well - a sort of gargling, bubbling sound intermittently destroys the music.

I tried Rhythmbox, and like it a lot, but it's having problems importing some of my music. On specific files (about 1 or 2 in every 100), it just hangs, and crashes. All the files are OK - I can play them in other apps.

Anyone got any ideas what could be causing either of these problems?

---

### Post by poofyhairguy on 2004-12-07
[QUOTE=adpsimpson]Hi, firstly thanks for a great distro. Having used Mandrake for over a year, I was getting fed up with the bugs and just ready to try a Debian-based distro, and just then Ubuntu stepped in... So far I have no complaints. Everything is incredibly stable, well configured etc. Preferring KDE to Gnome, I was amazed at how little hassle it was to install.

However I'm having one problem. I have a large number of mp3s, and have previously used Juk to play them, but it's not doing well - a sort of gargling, bubbling sound intermittently destroys the music.

I tried Rhythmbox, and like it a lot, but it's having problems importing some of my music. On specific files (about 1 or 2 in every 100), it just hangs, and crashes. All the files are OK - I can play them in other apps.

Anyone got any ideas what could be causing either of these problems?[/QUOTE]


Nope. I use Gxine, a media player ment for gnome. I've never had a single MP3 bork on me.

---

### Post by TravisNewman on 2004-12-07
The problem with rhythmbox is that it's trying to open a file that it doesn't support, usually a text, graphic, desktop.ini, thumbs.db, album art, etc, that gets included in downloaded music or alternatively downloaded by windows media player, etc etc. It appears it hangs on a song file, but it's actually hanging on the next file it tries to load. This is a known bug and is being resolved (or may already have in testing, i dunno)

Also, I notice the subject says something about Amarok, but you didn't mention it in your post. You can get it from universe, if that was your question. Just notice, it's spelled AmArok, not AmOrak

---

### Post by rolfpal on 2004-12-07
Hi,

I don't know if this is you problem but.

Rythmbox can't seem to understand if any other kinds of files besides audio files are in a directory that it is reading.

I have album covers (jpgs or pngs) in most music directories and so it hangs and is useless for me.

I use xmms (sigh), at least it is stable.

Cheers,

---

### Post by adpsimpson on 2004-12-08
Hi again, thanks for the replies. I see a similar thread is also under way... Well I've been through and deleted every non .mp3 file I can find, and still the same problem with rhythmbox. I've narrowed down at least one of the hang-points to track 13 of the Oceans 11 sound track - there is nothing wrong with this, and nothing else in the folder, so it seems like there's more to it than just .jpg files or whatever. Any more ideas?

GXine is really a video player, and doesn't seem to have the library facilities of juk or rhythmbox, which is what I'm looking for.

ps - I meant to put "Rhythmbox and Juk" in the title, but it was late!

---

### Post by nigelng on 2004-12-08
Why don't u guys try BeepMediaPlay [http://beepmp.sourceforge.net](http://beepmp.sourceforge.net) ) , a fork apps from XMMS, better code, better integration to Gtk2 (better interface).

Try it... anyway, as fork from XMMS, it inherite most features in XMMS, incl skins and some (not all) plugins

Nigel :mrgreen:

---

### Post by adpsimpson on 2004-12-08
If it's just an updated XMMS, it won't have the playlist, library and search features that set Rhythmbox and Juk apart. That's really what I'm looking for, but in the meantime I'll settle with XMMS.

Anyone know why Juk would sound so choppy though? Still working on that one. XMMS plays fine, including the specific mp3's that rhythmbox hangs on.

---

### Post by kmoz on 2004-12-10
[QUOTE=panickedthumb]
Also, I notice the subject says something about Amarok, but you didn't mention it in your post. You can get it from universe, if that was your question. Just notice, it's spelled AmArok, not AmOrak[/QUOTE]

I have enabled universe and multiverse, but a search of synaptic (or simply apt-get at a terminal) is unable to find amarok anywhere.  What universe server are you using?

---

### Post by adbak on 2004-12-10
Go to [http://www.apt-get.org](http://www.apt-get.org) and click on the link that says "search for a package".  Type in Amarok and you should get a list of sources that you can put (momentarily if you so desire) into your /etc/apt/sources.list.  That source should have Amarok, but it's not guaranteed to work as it's not an official repo.

---

### Post by GeneticFreek on 2004-12-11
[QUOTE=adpsimpson]Hi again, thanks for the replies. I see a similar thread is also under way... Well I've been through and deleted every non .mp3 file I can find, and still the same problem with rhythmbox. I've narrowed down at least one of the hang-points to track 13 of the Oceans 11 sound track - there is nothing wrong with this, and nothing else in the folder, so it seems like there's more to it than just .jpg files or whatever. Any more ideas?[/QUOTE]

I had trouble adding in my library of 6000+ songs to rhythmbox too, but found that if I added songs in smaller chunks (eg via artist by artist rather than the whole shebang at once). It would still get stuck once in a while, but I managed to add every song without deleting any extraneous files in the folders.

I did notice that it would hang more when it came across a file format it didn't like (.mpc, .ape). I think it may also have to do in part with the way the files are tagged. A lot of my files were tagged with the APE archetecture rather than id3 (I used to use foobar2000 in windows) and I think that may have been throwing it off from time to time if there was an odd tag.

Just my thoughts.

---

### Post by 00Vadim005683 on 2007-05-15
> **kmoz said:**
> I have enabled universe and multiverse, but a search of synaptic (or simply apt-get at a terminal) is unable to find amarok anywhere.  What universe server are you using?


[Credit Cards Britney Spears memory food science Yahoo](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/incest-porn.html)

---

