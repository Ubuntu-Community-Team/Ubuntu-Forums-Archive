---
title: "Amarok refuses to build &quot;My Collection&quot; past 3%"
date: 2006-10-15
forum: Desktop Environments
---

### Post by teiresias on 2006-10-15
Sorry if this doesn't belong in this forum, if I should post it elsewhere let me know.  This is my second shot at trying to get Amarok to work - the latest version available in the repositories (the backport repository anyway).

When I use Amarok 1.3 it works fine; however, Amarok 1.4.3 (I think that's the one currently in the Backport Repository) refuses to build my collection database.  It will scan and work up until the meter reaches 3%, at which point Ubuntu starts thrashing and it never gets past 3%.  The fact that it reaches 3% is rather constant as well, it always happens at 3%.  I'm not sure if it's thrashing the HDD or just stealing so many cycles from the CPU, but I end up having to force quit out of Amarok and then usually I have to reboot the PC to get the OS to recover to its normal operational speed.

At first I thought this was a problem because I originally built my library with 1.3 and then upgraded to 1.4, but on this new install of Ubuntu I installed 1.4.3 directly and it does the same thing.  All of my audio files are AAC or MP3 files, with no DRM, and both versions of Amarok can play all of my individual files fine, it just refuses to build the database.

Does anyone have any idea how I could diagnose and fix this.  I'd prefer to use Amarok due to its iPod support, but if i can't get it working I suppose I could put up with using gtkpod and a separate podcast subscriber.

Thanks to anyone who has any ideas.

---

### Post by orb9220 on 2006-10-15
For some reason it is choking on some files that it considers corrupt tags.
The way I track down bad ones is to go to prefs and in library to search I deselect all and start adding checks until I get to folder causing problems.

In my example I had mp3 checked which included all my folders by genre>artist>album.

So I deselect mp3 and started to check each genre folder and see if it makes it thru. When I find a choke point lets say alternative then I go in and deselect and add artists until it narrows down so on and so on.

It always seems to be tag information or a filetype I forgot was there.

---

### Post by teiresias on 2006-10-16
Thanks orb, I'll give that procedure a try when I get home.  In the meantime I've been trying out both "Listen" and "Exaile," the latter of which reads the entire library fine, so perhaps it's just more tolerant of tagging irregularities.

---

