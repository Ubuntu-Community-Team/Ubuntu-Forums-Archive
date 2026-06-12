---
title: "nautilus won't preview sound files on hover"
date: 2007-04-26
forum: Desktop Environments
---

### Post by TheRingmaster on 2007-04-26
For some reason nautilus won't preview my mp3's I have. Is there a reason for this. I know that this worked in edgy.

---

### Post by patrickfromspain on 2007-04-26
sudo apt-get install mpg123 or mpg321, don't remember now.

---

### Post by stchman on 2007-04-26
> **patrickfromspain said:**
> sudo apt-get install mpg123 or mpg321, don't remember now.

Does that work for .ogg and .wav files as well?  When I used Mandrake it started playing .mp3 files as I moused over them.  I personally found it annoying.

---

### Post by TheRingmaster on 2007-04-26
The weird thing is that this worked in edgy. I had a guy in irc saying that the feature doesn't even exist. I think he needs a wake-up call. :)

---

### Post by TheRingmaster on 2007-04-26
mpg123-alsa is the one that I chose and YES it worked. Thanks for the help and information.

BUT I still need to know how to get ogg and wav to do the same. ( I found a package (mention of it though) called ogg123, but I can't find it in the repos. What's the deal?)

---

### Post by dommyOZ on 2007-04-29
> **TheRingmaster said:**
> mpg123-alsa is the one that I chose and YES it worked. Thanks for the help and information.

BUT I still need to know how to get ogg and wav to do the same. ( I found a package (mention of it though) called ogg123, but I can't find it in the repos. What's the deal?)

Install vorbis-tools and that will give you ogg, I had to install sox to get wav to work and at the moment I'm stuck with flac can't find anything that works. This is all for Nautilus in Feisty 

Any one have an idea about flac??

---

