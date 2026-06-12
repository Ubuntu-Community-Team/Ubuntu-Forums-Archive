---
title: "MPD volume ignored"
date: 2009-06-19
forum: General Help
---

### Post by Nonno Bassotto on 2009-06-19
I recently installed Ubuntu 9.04 and immediately installed mpd. Everything works fine, but the MPD volume is ignored. I can set the general volume, but changing the volume level of MPD, even to 0%, does absolutely nothing. The configuration is the default MPD configuration. Any ideas?

---

### Post by Nonno Bassotto on 2009-06-19
Ok, solved. It is a problem with mpd <0.15 and PulseAudio. It is enough to uncomment the line

```

mixer_type "software"

```

in /etc/mpd.conf

---

### Post by supernes on 2013-01-21
This trick also worked on mpd 0.16.1 (Ubuntu Natty).

---

### Post by BlinkinCat on 2013-01-21
old thread

---

### Post by papibe on 2013-01-21
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

