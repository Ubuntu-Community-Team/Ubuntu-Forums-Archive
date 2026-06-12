---
title: "Which DVD ripper is the same as DVDfab for ubuntu?"
date: 2009-01-22
forum: General Help
---

### Post by Fastfwd on 2009-01-22
All I need is a DVD ripper that does a perfect copyon my hard disk of what is on the DVD. On windows right now only DVDfab does this since some new copy protection schemes broke some of the other software I was aware of.

I do not need to process the data at all. Just want a perfect copy so I can watch the movie from VLC without using the dvd-rom drive at all.

Suggestions?

---

### Post by Fastfwd on 2009-01-22
Forgot to say. Already did a search and found a thread about dvd:decrypter but that does not work with all kinds of copy protection.

Also don't need a way to make dvdfab work from within wine. I'll just book into windows or use vmware if I want that.

I'm wondering if there is a 100% linux solution to the copy protection problem on the DVDs. I don't want to make a copy to another DVD. Just watch it from my hard-drive instead of from the DVD drive.

I also sometimes use handbrake to make a version that will play on AppleTV but that I can easily do on my own once I have a good copy on disk.

Thanks

---

### Post by stchman on 2009-01-22
You can try K9copy or AcidRip.  I use K9copy as it has a more intuitive interface.

---

### Post by hyper_ch on 2009-01-22
you could use dd from the command line

Not sure if it needs sudo or not. If it doesn't (what I think) run:

```

dd if=/dev/sde of=~/Desktop/dvd.iso

```

if it requires sudo, run:
```

sudo dd if=/dev/sde of=/home/USER/Desktop/dvd.iso
sudo chown USER.USER /home/USER/Desktop/dvd.iso

```

Then you can right-click the .iso file and select it to be opened by vlc.

This assumes, that the dvd drive is /dev/sde

---

### Post by mc4man on 2009-01-22
Here's a couple of posts concerning such.

[http://ubuntuforums.org/showthread.php?t=975691&highlight=rip](http://ubuntuforums.org/showthread.php?t=975691&highlight=rip) (10)

> Just want a perfect copy so I can watch the movie from VLC without using the dvd-rom drive at all.

[http://ubuntuforums.org/showthread.php?t=1010331&highlight=dvdisaster&page=2](http://ubuntuforums.org/showthread.php?t=1010331&highlight=dvdisaster&page=2) (19)

Above will do **any** title that can be played back, will dump to an encrypted .iso with structure protection intact (irrelevant to playback.
The only determining factor for s.p. is the number of unreadable sectors skipped, if there are huge #'s then a waste of time. Figure about 1.5 sec.'s per block of 16 sectors.
Good only for playback, cannot be burnt or processed (involves no bypassing of copyright protection whatsoever

---

### Post by nikgare on 2009-01-22
**vobcopy** has always worked for me in the past

---

### Post by zisun666 on 2009-02-25
[FreeStar Free DVD Ripper]("http://www.free-star.org/free-dvd-ripper-freeware.html") would be you find, it work fine on ubuntu same as on win***. I had ripped some copy protection DVD to divx AVI success.

---

### Post by teejcee on 2011-09-28
OK, I've downloaded Freestar Free DVD Ripper for linux.

It's not a deb file. Can anyone tell me how I go about installing this? 

Thanks.

---

### Post by howefield on 2011-09-28
Hi, please start a new thread rather than tacking on to the end of a two and a half year old one.

To be honest, I'd be sure there are better (supported) ways to achieve your aim than using this application.

---

