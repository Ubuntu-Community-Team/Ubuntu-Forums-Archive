---
title: "FreeCiv 2.1 Beta: Must I compile it myself?"
date: 2007-03-11
forum: Gaming &amp; Leisure
---

### Post by Mr. Picklesworth on 2007-03-11
I've become interested in getting going with Freeciv (which is difficult for me because I am very picky), and I just discovered that the in development 2.1 beta seems to look 100 times nicer than the stable version thanks to this new-fangled Themes thing (or at least the Human theme -- I really have no clue what's new and what's old here, all I know is that I am incapable of getting 2.0.9 to look as pretty as those new screenshots).
I /could/ download from SVN and compile overnight via my awful 500 mHz box, or maybe someone here already has done so, has it compiled and / or knows how to make .debs? (Or do you know of a build already available?)

Thanks!!!

---

### Post by po0f on 2007-03-11
Mr. Picklesworth,

I could upload a checkinstall deb if you'd like.  Of course, I'd have to compile it first, but if you're interested, holler back.

---

### Post by Mr. Picklesworth on 2007-03-11
Ooooh, I did not know about CheckInstall. Thanks for telling me about it :)

Thanks for the offer.
It's going now (was a lot less painful than I had been expecting after the bother needed to get Epiphany compiling) and I'm about to go to sleep though, so no need. I'll post a link to the deb if it works and isn't too huge. (I'm just building the SDL version for now, though).

---

### Post by po0f on 2007-03-11
Mr. Picklesworth,

Yeah, checkinstall helps keep your system clean.  :)

A default './configure' produced an 8.4M deb for me, that's why I wanted you to reply if you wanted it or not.  I didn't feel like uploading it just because.  :)

---

### Post by Mr. Picklesworth on 2007-03-12
Alright, I have two Debian packages for FreeCiv 2.1.0 Beta 3: One with the SDL client, one with the GTK client.
Playing with the SDL version I can see that it is magnitudes more pretty (and it is /very/ pretty!) with a much better designed interface overall. However, this comes at a price: It is slower! This slowdown probably won't be noticed by most, but on my horrible computer here it can be evident. The SDL mode is certainly a bit buggy, for example when I was playing with it there was a tiny window that just would not close.
I haven't actually tried the GTK version, but I have created and installed its deb.

Use at your own risk: I have no idea what I am doing and these debs are probably not created in the most reliable way. You cannot install both at once: If you want the SDL client, make sure to uninstall the GTK client first. (And vice versa).

Anyway, enjoy!
[SDL Client](http://dylanmccall.googlepages.com/freeciv-sdl_2.1.0-beta3-1_i386.deb)
GTK Client coming soon. (Sorry, I'm on wireless).

I'm storing this on Google Pages, which is still in Labs, so be gentle. (Very picky, undisclosed bandwidth limit).

As for when those downloads will be up, I can't be sure. It's still uploading that SDL one I linked to and I'm about to go to sleep, then I'm going away for a week so the GTK one will not be up for a long time.
Er... it might work.


Edit:
Sorry, links are both broken. I just realized I'm back, though, and I still have the debs, so if you can't wait for the beta to end I'll try to get them uploaded some time in the next 10 hours.

---

### Post by teddybairs on 2007-03-15
If at all possible, I'd be interested in a link to a freeciv 2.1 deb as well. I'm an Ubuntu user but have absolutely no real success in anything I've tried to compile, and it just sucks that the freeciv people seem to think that all Linux users automatically compile their own packages.

---

### Post by lulin on 2007-03-25
[Here]("http://www.megaupload.com/de/?d=5Q7B0TWN") is the GTK version.

---

### Post by charlieg on 2007-04-03
I posted .debs for freeciv-2.1beta4 here:
[http://www.ubuntuforums.org/showthread.php?t=399516&highlight=freeciv](http://www.ubuntuforums.org/showthread.php?t=399516&highlight=freeciv)

---

