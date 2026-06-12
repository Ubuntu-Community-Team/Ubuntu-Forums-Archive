---
title: "mod, s3m to mp3.."
date: 2006-09-23
forum: Desktop Environments
---

### Post by kimara on 2006-09-23
hi

I like to convert mod and s3m songs to mp3.

Is there any programs to linux which would do this?

Thanks..

---

### Post by Kelan on 2007-12-27
When I used Gentoo, I used the following script:

  dumb2wav $1 -o audiodump.wav
  lame audiodump.wav $2
  rm audiodump.wav

Now that I'm back to Ubuntu, though, I'm not sure what package (if any) the "dumb2wav" program comes in (it isn't libdumb), sorry.

---

