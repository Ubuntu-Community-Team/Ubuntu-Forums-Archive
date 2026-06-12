---
title: "No sound in Youtube videos (9.04)"
date: 2009-06-02
forum: General Help
---

### Post by Shelbsterina on 2009-06-02
After I upgraded to Jaunty, I actually had no problems with Youtube videos or anything in Firefox at all. This new Amarok 2 is what I had issues in to begin with (Music would play, but no sound). After some Googling, I found a solution. So Amarok works fine now, but Youtube videos play without any sound.
To solve my issue with Amarok, I installed:

```
ubuntu-restricted-extras
```

```
phonon-backend-gstreamer
```

```
phonon-backend-xine
```

Would any of those cause any conflict with sound coming from Firefox? Is pulseaudio trying to hog up my sound card again? What's going on here?

---

### Post by Tipped OuT on 2009-06-02
I think it's because, in order to play music with Amarok you must use the Xine sound engine... (which was your "fix") I guess it doesn't work for flash audio?

I would suggest undoing the "fix" and using Rhythm Box or Banshee. :)

---

### Post by cak3 on 2009-06-02
That issue also appears when flash (ie the youtube vids) cant access the sound since that sink is already taken by something else (such as amarok), something that Pulseaudio was meant to fix, but it can be somewhat difficult to get that working in some situations. 

Is your installation 64-bit? I know there are difficulties with flash 10 and x64_86 linux. There is a guide for that here: [http://meandubuntu.wordpress.com/2008/11/18/real-64-bit-flash-on-amd64/](http://meandubuntu.wordpress.com/2008/11/18/real-64-bit-flash-on-amd64/)

---

### Post by Shelbsterina on 2009-06-02
Yeah, I have the 64-bit. Thanks, I'll take a look at that.

---

### Post by Shelbsterina on 2009-06-02
Alright, I figured out what was wrong and everything works now. For anyone else who has this problem, I went into "Sound" and changed Music and movies to ALSA, and system events to OSS. That's all!

---

