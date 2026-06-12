---
title: "Dvd not playing video, quits when open VLC"
date: 2006-07-07
forum: Desktop Environments
---

### Post by birch on 2006-07-07
I have using ubuntu for a little while now and I recently just upgraded to Dapper Drake (clean install).  Now my DVD's will not play.

I believe I have all the right codecs and everything (libdvd, etc).

I set VLC to play dvd's and when I put a dvd in it plays for a few seconds and then stops and quits, not enough time to see any video.
It does the same thing when I try to just play the .VOB files too.

VLC work perfect for other media (xvid,mp3's mov).

I've tried other players totem, mplayer, xine, none will play DVD's.  Xine will play the dvd but it only plays the audio not the video.

I feel the problem is in the codecs but I feel I've tried everything in the tutorials and it still doesn't work.  The dvd player seems to function correctly (ejecting and reading)

Any ideas???? (I've already tried reinstalling the codecs)

DVD player:
IDE device (slave)
Toshiba dvd-rom sd-m1212

Thanks

---

### Post by vem0m on 2006-07-07
did you get the restricted libdvdcss2? For more info [Click Here]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by birch on 2006-07-09
yes I did.

Like I said I'm not a total newbie, and I have used linux to play dvd's on Breezy, it just doesn't work now on dapper very strange

any other ideas?

thanks for the response

---

### Post by birch on 2006-07-11
ok so I got it working after readaing:

"I solved the problem by starting xine with a
video driver other than Xv. i.e. start xine like this:
xine -V XShm"

but how do I get that to work everytime? or make it so xine does not use Xv?

---

