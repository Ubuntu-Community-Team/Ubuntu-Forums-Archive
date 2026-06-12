---
title: "Totem/xine/dvdcss not playing LOTR:Return of the king se disc1"
date: 2005-01-13
forum: Desktop Environments
---

### Post by Poldi on 2005-01-13
I know this is completely unsupported, but somebody here might still be able to help me:

I exchanged Totems GStreamer backend with Totem-Xine and installed libdvdcss from the additional repository mentioned in the howtos.

I can play all my DVDs just fine with one exception being LOTR: Rotk, special edition DVD no. 1.

the other lotr-DVDs play fine and the second rotk disc plays as well. 

the error message says something about libdvdcss not available or unable to decode. the dvd-title features strange character symbols as well (this goes for all lotr-dvds, but only this one has problems in viewing). I use a german Ubuntu (Warty + very few .debs), german DVDs and have reconfigured the system to use UTF-8.

anybody seen this before? with a solution at hand?

kind regards,
Carsten

---

### Post by wulf on 2005-01-13
I recently got *LOTR:ROTK special edition* and it played okay on my set up (gxine + libdvdcss). However, it might have been this disk that threw up some errors on the console (I'm in the habit of firing up gxine from a console so I can see the messages it thows up)... I'll try to remember to check tonight or tomorrow morning.

Wulf

---

### Post by wallijonn on 2005-01-13
For me, ROTK, DVD#1 works fine in Totem-xine and Xine. MPlayer dies, of course, because it cannot deal with the menu system. I have [COLOR=Blue]libdvdcss2_1.2.8-1_i386.deb[/COLOR] installed over some older codecs, [COLOR=Blue]libdvdcss2_1.2.8-sarge0.0_i386.deb[/COLOR] (which is basically the same codec) and [COLOR=Blue]libdvdcss1_1.0.1-0.1_i386.deb[/COLOR].

Do you have the 1_1.0.1_i386 file or the 2_1.2.8-1_i386 file?

---

### Post by hardcandy on 2005-01-13
And if that does not work, maybe look in the FAQ/Howto about using Ogle for playing DVD's. I have mplayer, xine,ogle, VLC all installed.

Also, was this a copy purchased in a store, a copy, or one downloaded from newsgroups, p2p, etc?

---

### Post by mark on 2005-01-13
Having piqued my curiousity, I just tried my copy of LOTR:ROTK "Special Extended" version & it plays correctly in xine.  My libdvdcss2 version is identical to wallijonn's.

---

### Post by wulf on 2005-01-13
The console message I got while the menu was showing was as follows:

```
libdvdnav: Language 'en' not found, using 'ÿÿ' instead
libdvdnav: Menu Languages available: ÿÿ
```

That repeats several times while the menu is showing but not, during my limited testing, when the movie itself is playing. Maybe it's encoded in Quenya... ;)

Wulf

---

### Post by Poldi on 2005-01-13
[QUOTE=hardcandy]And if that does not work, maybe look in the FAQ/Howto about using Ogle for playing DVD's. I have mplayer, xine,ogle, VLC all installed.
[/QUOTE]

I really think this has to do with libdvdcss & internationalization, not a specific player.

> 
Also, was this a copy purchased in a store, a copy, or one downloaded from newsgroups, p2p, etc?

what do you mean - Ubuntu or LOTR? :-) the DVDs are fresh from store.

I have now installed the  libdvdcss1_1.0.1-0.1_i386.deb package that I did not have before (along with libdvdread2). makes no difference.

trying with gxine does not work as well.

what I get (ever with Totem) is the very first "Warner Bros." splash with sound and all. after that libxine/libdvdcss fail me. i cannot play the .vob files either.

thanks for all who tried to help, but as it stands, I can only see 5/6 of the saga. :-(

---

### Post by wallijonn on 2005-01-13
Wulf,

> 
libdvdnav: Language 'en' not found, using 'ÿÿ' instead
libdvdnav: Menu Languages available: ÿÿ


The obvious question then becomes, "did you install or re-install [COLOR=Blue]libdvdnav[/COLOR] and [COLOR=Blue]libc6[/COLOR]?

English navigation language not found? hmmm.

---

### Post by danip on 2005-01-13
sudo apt-get install gnome-vlc 

totem wont play alot of my dvds but vlc runs them fantastic

---

### Post by wulf on 2005-01-14
[QUOTE=wallijonn]The obvious question then becomes, "did you install or re-install [COLOR=Blue]libdvdnav[/COLOR] and [COLOR=Blue]libc6[/COLOR]?

English navigation language not found? hmmm.[/QUOTE]
Pass. I set it up a month or so ago and I can't remember the exact steps I took. As I recall, it went very smoothly once I'd set up the "restricted formats" repository mentioned in the relevant WIKI page so that I could get the right libraries.

I don't have any problems with playback - just an odd message repeated a few times on my monitoring console. I don't recall seeing it from other disks - I suppose it might be a good idea to check LOTR:ROTK disk two and see what happens.

Wulf

---

### Post by Quest-Master on 2005-01-14
[QUOTE=wulf]Pass. I set it up a month or so ago and I can't remember the exact steps I took. As I recall, it went very smoothly once I'd set up the "restricted formats" repository mentioned in the relevant WIKI page so that I could get the right libraries.

I don't have any problems with playback - just an odd message repeated a few times on my monitoring console. I don't recall seeing it from other disks - I suppose it might be a good idea to check LOTR:ROTK disk two and see what happens.

Wulf[/QUOTE]
 If you haven't yet, try Ogle as well. Vlc is another good choice.

---

### Post by Lynx on 2005-01-15
I use Ogle and it works quite well. I am very pleased with it. I used it suse and it is just as stable and dependable in Ubuntu.

---

### Post by wulf on 2005-01-15
What advantages does ogle have over gxine, since the latter "just works" on my machine?

Wulf

---

### Post by ixus_123 on 2005-01-16
You might want to try downloading **[http://www.geexbox.org/en/index.html](http://www.geexbox.org/en/index.html)** to test things out.  Basically it's a basic live CD consisting of mplayer & ther bare essentials of Linux.  It's only a 6mb (six) download if i remember correctly & atleast you'll be able to tell if the problem is just a bad disk or if maybe something has got corrupted on your computer.  It's a lot easier than testing other things out

[http://www.geexbox.org/en/index.html](http://www.geexbox.org/en/index.html)

---

