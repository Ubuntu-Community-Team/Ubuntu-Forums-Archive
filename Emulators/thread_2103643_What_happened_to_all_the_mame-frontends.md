---
title: "What happened to all the mame-frontends?"
date: 2013-01-10
forum: Emulators
---

### Post by ZarathustraDK on 2013-01-10
I'm building a cabinet for mame and have been checking out various frontends for it.

The frontends in the repos (gmameui and gnomecab (I think it was called)) are both for desktop-use, not really cabinet-material.

Wahcade hasn't been updated in 3 years, and the package download raises a lot of "bad quality"-flags when trying to install.

Cabrio FE relies on old libraries (libavcodec-52 and libavutil-52).

That only leaves AdvanceMenu which I have to compile myself.

Do you guys know of any frontends for linux out there that would be good for a cab?

---

### Post by beeris on 2013-01-31
I was in the same boat a few weeks back. I settled on getting cabrio working. It's worth the effort in my opinion. The old libraries aren't hard to find and if you follow the install instructions it should work. I found that I had to use the git repo, not the source that is posted on the cabrio site. The cabrio google group has some good info on compiling as well. Good luck!

---

### Post by naxil on 2013-12-15
beeries where u find the cabrio old lib? compiling is very difficult.. the site provide the web but my ubuntu is 12.04 and deb askme for libavcodec52 (>= 4:0.6-1~)|libavcodec-extra-52 (>= 4:0.6-1~) where i findit?

---

