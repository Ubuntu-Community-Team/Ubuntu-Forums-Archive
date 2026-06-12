---
title: "login sounds"
date: 2009-04-24
forum: General Help
---

### Post by JakeHinojosa on 2009-04-24
i posted something like this about a week ago, but ill just do a repeat of it.
Right now, my login sounds are disabled. if i enable them, no other uadio works when im logged in. those are the only sounds i am able to hear. but when i disable login sounds, the audio works. i want to have login sounds enabled, but not it being the only sounds im able to hear while using the computer. i tried to do a re install of ubuntu. did nothing. is there a way to fix this?

---

### Post by paradigm2 on 2009-04-24
I had issues where 30% of the time my system would lock up on the login sound.  I had to upgrade the kernel (9.030rc2 or later), pulseaudio, and alsa to non-ubuntu-supported versions in order to fully fix it.

You may or may not need to do that.

```

lspci

```

What sound hardware have you so we may check for hardware dependent issues?

---

