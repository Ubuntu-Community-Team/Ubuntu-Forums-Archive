---
title: "q3jack/joss sound?"
date: 2006-07-03
forum: Gaming &amp; Leisure
---

### Post by pharcyde on 2006-07-03
I've tried using q3jack 0.2 and joss 0.3.  I can get both to successfully compile and install but cannnot get them to work.  Below is what I try to do.

I first run
```
jackd -R -o oss &
```
then
```
joss ./quake3
```
but I get no sound in quake 3 and this is printed in the q3 console
```

/dev/dsp: Device or resource busy
Could not open /dev/dsp

```

---

### Post by RawMustard on 2006-07-04
try  jackd -d oss & joss quake3  It works for me, but my sound is a little bit of static.  I'm now trying figure out how to get rid of the static.  It's quite playable tho :)

---

### Post by fakie_flip on 2007-01-22
How did you get joss to compile? I can not get it to compile. I have jackd in the repos, so I do not need to compile it. I have the dsp error. I was able to fix it before with
sudo 'echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss'
But that does not work anymore :( I do not know why it quit working.

---

### Post by fakie_flip on 2007-01-22
> **RawMustard said:**
> try  jackd -d oss & joss quake3  It works for me, but my sound is a little bit of static.  I'm now trying figure out how to get rid of the static.  It's quite playable tho :)

Were you able to get rid of the static? I tried aoss et, but the sound was very choppy.

---

