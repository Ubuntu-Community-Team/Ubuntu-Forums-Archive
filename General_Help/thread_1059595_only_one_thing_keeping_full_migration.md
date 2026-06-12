---
title: "only one thing keeping full migration"
date: 2009-02-03
forum: General Help
---

### Post by Z3r0t0l0rEnCe on 2009-02-03
I have only one thing that is keeping from a complete migration.  It would be encoding and burning movies.  I've been using DVDFlick on M$ and want to stop using if I could figure out how and which application I should use in Ubuntu 8.10.  I'm still new so be detailed in how and what I need to do. Thanks everyone.

---

### Post by jerome1232 on 2009-02-03
Handbrake is awesome if you ask me (for transcoding dvd's)

[http://handbrake.fr/](http://handbrake.fr/)

and DeVeDe for generating burnable iso's out of movie files, it's in the repo's

---

### Post by HuaiDan on 2009-02-03
Ubuntu's native Brazero has always worked flawlessly for me.

---

### Post by mb_webguy on 2009-02-03
As far as applications, you should try Handbrake or OGMrip, both of which are in the repositories.  If you like matroska files with h.264 video and AC3 audio, then OGMrip is your friend.  If you want device-compliant avi files (to play on an XBox 360, PS3, or other DivX-compliant media player) with xvid or h.264 video and AAC audio, go with Handbrake.  

You'll need to add the [Medibuntu repository]("https://help.ubuntu.com/community/Medibuntu") and install the libdvdcss2 package to play encrypted DVDs.  You'll also want to install the extra codecs.  

You may also want to compile your own x264 and ffmpeg packages for better performance and increased codec support.  If so, check the link in my signature.

As far as creating DVDs, check out DeVeDe, which is in the repos, and ManDVD, which you can get from GetDeb or [this PPA]("https://launchpad.net/~quadrispro/+archive/ppa").

---

### Post by KeyserSoze93 on 2009-02-04
I suspect most encoding software for Ubuntu uses ffmpeg or mencoder as a backend. Mencoder is a command line program, but it's very easy to use. For example, to encode a reasonable quality DivX movie from a DVD in the default drive, just run:

```

mencoder dvd:// -ovc xvid -xvidencopts bitrate=750 -oac mp3lame -o "out.avi"

```

If mencoder isn't installed, just run:

```
sudo apt-get install mencoder
```

Check online for more guides if you want, but that does fine for most stuff. If you need smaller files, or better quality, just tweak the bitrate.

---

### Post by mb_webguy on 2009-02-04
As an addendum to KeyserSoze93's post...

Some transcoding applications rely on ffmpeg rather than mencoder.  The version of ffmpeg in the repositories doesn't support h.264 video or aac audio by default, though it's supposedly compiled with such support if you have the libraries.  So if you're using an app that relies on ffmpeg and you're trying to convert to h.264 video and/or aac audio, it will fail.  You'll have to (at minimum) install the "unstripped" libraries (libavcodec-unstripped-51, libavdevice-unstripped-52, libavformat-unstripped-52, libavutil-unstripped-49, libpostproc-unstripped-51, and libswscale-unstripped-0).  If that doesn't work, you'll need to compile ffmpeg with h.264 and aac support as I mentioned in my previous post.

---

### Post by Z3r0t0l0rEnCe on 2009-02-04
I will try out what you guys have posted and will get back to you today. thanks guys.

---

### Post by Z3r0t0l0rEnCe on 2009-02-04
I probably should of been more specific in what I was doing.  I use pirate bay for all my movies mostly. After I get the file I want to burn them to disk to watch on my xbox 360 or any compatible dvd player.  I know that DVDFlick did everything I need in MS.  But I just got done using HandBrake.  Now do I need to use DeVeDe(which I already have) to burn onto DVD-R or can I take the completed file from HandBrake and burn it to dvd?

---

### Post by Z3r0t0l0rEnCe on 2009-02-05
Well I used HandBrake and then DeVeDe and it didn't work.  I've also read both docs and watched some videos on YouTube just to make sure I did it right and nothing. Need a little more help.

---

### Post by jhayes on 2009-02-10
oh um yeah, i love dvdflick too.
but it works ok under wine, you should try it that way for now.
just make an iso, and burn the iso under linux.

---

