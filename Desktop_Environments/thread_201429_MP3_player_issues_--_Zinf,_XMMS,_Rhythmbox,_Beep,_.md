---
title: "MP3 player issues -- Zinf, XMMS, Rhythmbox, Beep, Banshee"
date: 2006-06-21
forum: Desktop Environments
---

### Post by Kensey on 2006-06-21
I've been having a heck of a time finding a music player that I like under Linux.  (Not a new thing; it goes back to my first desktop Linux days in late 1999.)
[LIST]
[*] Zinf is closest.  It's soooooooo close... but appears to have a real showstopper bug: it doesn't like directories whose names end in a dot.  When having it search my MP3 directory for music, it refused to traverse into the "R.E.M." directory (a major pain, since R.E.M. is my favorite band and thus disproportionately represented in my collection!)  And it didn't traverse into the "Vs." album directory under "Pearl Jam".  Even attempting to add those tracks manually failed: when I imported "Animal.mp3" from that directory, it created a listing for a file name "VsAnimal.mp3" and then wouldn't edit the info (obviously) because the file didn't exist.  Zinf is also, to all appearances, abandonware: the version I have installed is 2.2.5, which is the latest version, which was released better than 2 years ago.  I submitted a bug, but don't hold out a lot of hope on that score.

[*] XMMS: the default interface is absolutely opaque.  I remember the old WinAmp that XMMS imitated, and this is no WinAmp.  I guess I could find a better skin for it, but it leaves such a bad taste in my mouth I don't even feel like making that much effort.  It also doesn't seem to have a concept of a "library" as much as "select a bunch of tracks or a playlist out of a directory and I'll play that" (which doesn't really give you access to ID3 metadata like track length during the selection process).

[*] Rhythmbox for some unaccountable reason slows the UI to a crawl when I open it.  The mouse moves smoothly but there's a long delay (~2 seconds) when I click on anything in the Rhythmbox window before it reacts.

[*] Beep: see XMMS.  A little better interface-wise, but still has its annoyances: If I click on the D that double-sizes XMMS, Beep just scrolls the message "** DOUBLESIZE HAS BEEN REMOVED **".  So helpful to remove the function and leave the trigger.  See also XMMS complaints, of course.

[*] Banshee: Of course we're talking about the iTunes interface now, which is fine, but there are deficiencies here as well.  For example, I can sort by Artist, *or* Album Title, *or* track number, but I can't sort by Artist, then Album, then Track (i.e. a hierchical sort).  This is annoying to say the least.
[/LIST]

So now that I've complained about every one of the popular music players, what do people recommend?  I can almost get behind XMMS, but I would need a good skin recommendation.

What I want is basically Zinf without that annoying bug:

[LIST]
[*] A library and an easy way to automatically add new tracks to it.
[*] Hierarchical sorting of the library (tree view or list view, I don't care, as long as I can have multiple sort conditions) with options to also display metadata (at minimum artist, album, title, track length, and track number).
[*] An interface that allows for easy self-discovery.
[*] A couple of spiffy visualizers would be nice too.
[/LIST]

---

### Post by lindyslack on 2006-06-21
Have you tried amaroK? I like about the same as iTunes in windows with the added bonus of it showing lyrics too... Kinda cool... I don't really ever sit and read lyrics when listen to tunes while working but... It's kinda cool... I think I used Automatix to install amaroK... It's availabel at [http://www.getautomatix.com/]("http://www.getautomatix.com/") ... Directions are on that page too!

---

### Post by th3james on 2006-06-21
Another vote for amaroK, its the best music player ive ever used (on any OS), I love it. Make sure to get the newest version from the website

[Get amaroK]("http://kubuntu.org/announcements/amarok-1.4.php")

---

### Post by adam.skinner on 2006-06-21
[Exaile!]("http://www.exaile.org/") is also nice (basically an Amarok clone for GTK).

---

### Post by Kensey on 2006-06-21
I like it, I like it!  I'm trying amaroK right now.  Interestingly it seems to pick up three more tracks than Banshee did (no earthly idea why, I'll have to look into that).  I'll look into Exaile too -- it's always nice to see GNOME keeping up. :D  Further suggestions are of course more than welcome ;)

---

### Post by stengah on 2006-06-22
I'm an audiophile perfecto like yourself - Tried every player on the planet on every platform... now I'm running linux and thats how it's going to be. Depends on your criteria I guess... the best player I've tried so far is AmaroK - excellent player in every aspect. For me radio support is critical as well for my dose of groovy salad... paired with effortless handling of huge libraries. AmaroK does so... For Gnome the equivalents would be Listen or Exaile (the latter very beta I think - but try it out!)

Pretty sure the next HOT thing is goint to be Songbird developed by pioneeers of the inevitable- it's based on the mozilla engine and I think it has all the potential in the world to kick ***...

The linux port should be out soon - but damn; I'm not getting any younger here:-)

---

