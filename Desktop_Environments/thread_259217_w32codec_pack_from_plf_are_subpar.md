---
title: "w32codec pack from plf are subpar"
date: 2006-09-17
forum: Desktop Environments
---

### Post by McQuaid on 2006-09-17
I originally installed my w32codec pack way back in hoary by adding the marillat sources.  I don't like to mix sources at all but at the time it was the only way to grab that package through apt so I added marillat sid source just for that package and promptly removed the source.

So I haven't updated my w32codec pack in a long time.  I noticed HD content wouldn't play in mplayer.  I read this had something to do with needing a new mplayer version but also read conflicting things that it was a codec issue.

So I added the plf source and 'updated' the w32codec pack.  HD plays now but I also updated mplayer so that might have fixed that.  I thought all was well but I noticed some wmv stuff I have that used to play in mplayer no longer does, I only get the audio and mplayer at the cmd line even flags me saying I need to update my codec pack.

So it seems using the plf pack is a mixed bag.

I did a search on apt-get.org/search and see marillat still has his package  so I guess I can grab that but it still hasn't been updated:

w32codecs 1:20050412-0.4 (i386)

I also noticed another debian source [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/) that has this version:

w32codecs 1:20060611-0.0 (i386)

which is dated the same as the plf version so I assume this is going to have the same issues I do now.  Is there another updated package that doesn't loose playback ability of some wmv files that the 20050412 version could play?

---

### Post by dyssident on 2006-09-27
well plf is dropping ubuntu support and marillat doesnt seem too interested in making sure packages work in Ubuntu, but i can tell you that the latest from marillat's debian-multimedia.org work for me.

---

