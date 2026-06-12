---
title: "Xine and encrypted DVD's"
date: 2006-03-10
forum: Desktop Environments
---

### Post by smittyfree on 2006-03-10
How might I go about getting Xine to playback dvd's? I get as far as the fbi warning about don't illegally copy (I didn't, i put in a dvd of "Mission To Mars" that I bought last year) and Xine tells me it was stopped because the dvd was encrypted.

I got libdvdcss installed, but how can i activate it?

---

### Post by shamrock_uk on 2006-03-10
Hmm...if it's installed then it's activated as it's just a passive library. How exactly did you install it - you will have needed to add another repository, yes? What's the exact error message?

---

### Post by smittyfree on 2006-03-10
I installed libdvdcss-1.9.2 by downloading the tarball and compiling and installing it with the terminal. But Xine gives this message "xine engine message: 'Encrypted media stream detected Media stream scrambled/encrypted' " So i was wondering how to get xine to recognize libdvdcss.

---

### Post by shamrock_uk on 2006-03-10
Try this as an alternative:

```
sudo apt-get install libdvdread3
```

(just in case you haven't already)

Then type:

```
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
```

which will do the job for you. Just tested it now.

Sorry, I would try and figure out why your compile didn't work but I can't remember for the life of me where exactly libdvdcss is supposed to end up. I've been spoilt by apt-get for too long! :)

---

### Post by smittyfree on 2006-03-10
Oh no, It worked. It compiled sucessfully. Some of the files popped up in usr/local/lib. And I have libdvdread3. Xine will play the dvd just fine, except for the encryption.

---

### Post by smittyfree on 2006-03-10
I did what you told me, and now it gets past the fbi thing, then the touchstone logo/music comes up. Then it goes away, and the Xine Logo is there. So, it must work, but how do I get into the meno from there? I can't find it for the life of me. 


EDIT:
Oh, now it does the touchstone thing, and I get:
"xine engine failed to start.

No demuxer found - stream format not recognised."
Strange...

---

### Post by shamrock_uk on 2006-03-10
Even after you executed the script in my post (which installs from a .deb)?

Hmm...I've just tested it in xine and it seems to have picked it up for me. Have you altered the paths for libraries in the xine preferences? What does mplayer make of it?

I wonder if /usr/local/lib may be your problem - on my system they're in 

> /usr/lib/libdvdcss.so.2 
 /usr/lib/libdvdcss.so.2.0.4 

You could try pointing xine towards your /usr/local/lib/ folder, or maybe try moving yours into the main lib folder. 

Running the script above should put them in their correct place though.

---

### Post by smittyfree on 2006-03-10
Just in case you missed this: EDIT:
Oh, now it does the touchstone thing, and I get:
"xine engine failed to start.

No demuxer found - stream format not recognised."
Strange...

And Mplayer wont even start playing.

---

### Post by shamrock_uk on 2006-03-10
Ah, looks like we crossed posts. :)

Your second error looks like a codec problem. Try this:

```
  wget -c ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb
  sudo dpkg -i w32codecs_20050412-0.0_i386.deb
```

Edit, try using apt-get for these as well (the filename may be slightly different):

> libmpeg2-4 
libsmpeg0   

It may simply be an mpeg problem: I seem to remember these not being installed by default in Ubuntu. (Sorry, I have no idea how much you have installed or your experience level here)

---

### Post by smittyfree on 2006-03-10
Well, I've been using Ubuntu for a month or two now, and This pc is the first computer that is only linux that I've used. I'll try your suggestions.

---

### Post by shamrock_uk on 2006-03-10
Ah ok, when you dived into tarballs I assumed you'd been using Linux a little longer than that! 

Welcome to the fold :)

Whilst I would thoroughly recommend getting your 'hands dirty' as that's where the fun learning is to be had, if you ever want things like this to "just work", you could do a lot worse than [Automatix](http://ubuntuforums.org/showthread.php?t=138405) which is a wonderful timesaver if you have a fast connection. (Edit, corrected wrong link)

---

### Post by smittyfree on 2006-03-10
O well, I can't get the dvd to play, good thing I have a dvd player hooked up to my TV.

*EDIT: Well, VLC will play it now, but the sound skips and the framerate is less than satisfactory. (this is post Automatix)*

---

### Post by shamrock_uk on 2006-03-10
Try mplayer now, that's normally the nippiest for me. 

If it's skipping then check whether [DMA is enabled](https://wiki.ubuntu.com/DMA) for your dvd drive (can also be done via automatix). It being turned off is the most likely cause for the skipping and the sound problems. 

At least you're halfway there ;)

---

### Post by smittyfree on 2006-03-10
AH! DMA! I forgot about that, lets see if I can...OH SNAP! That worked! Now I just gota figure out how to keep it enabled..

---

### Post by shamrock_uk on 2006-03-10
[QUOTE=smittyfree]AH! DMA! I forgot about that, lets see if I can...OH SNAP! That worked! Now I just gota figure out how to keep it enabled..[/QUOTE]
As per the wiki article:

```
   /dev/hdc {
   dma = on
   }
   
```

Just paste that into your hdparm.conf file.

```
sudo gedit /etc/hdparm.conf
```

Glad it's all working..bed time for me now :)

---

### Post by smittyfree on 2006-03-10
Done and Done. Thanks shamrock. This case is SOLVED.

---

### Post by ekravche on 2006-03-11
[QUOTE=shamrock_uk]Try this as an alternative:

```
sudo apt-get install libdvdread3
```

(just in case you haven't already)

Then type:

```
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
```

which will do the job for you. Just tested it now.

Sorry, I would try and figure out why your compile didn't work but I can't remember for the life of me where exactly libdvdcss is supposed to end up. I've been spoilt by apt-get for too long! :)[/QUOTE]

worked like a charm! Thank you for the help

---

