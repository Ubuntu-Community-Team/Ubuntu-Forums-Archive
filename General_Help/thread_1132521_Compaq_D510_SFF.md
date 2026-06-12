---
title: "Compaq D510 SFF"
date: 2009-04-21
forum: General Help
---

### Post by shaneprice on 2009-04-21
I have a Compaq D510 SFF. It has internal speakers. I cannot get my external USB speakers to work as a result. I have switched my sound preferences to USB (OSS), and the test button it produces sound through the USB speakers when pressed. ALSA however will not work at all. Any ideas?

I am running Ubuntu 8.10

---

### Post by shaneprice on 2009-04-22
Ok, please someone?

---

### Post by shaneprice on 2009-04-24
This is suppose to be where I can come to get help? Do I have to scream for it, say a secret password, secret handshake what?

---

### Post by jamessnell on 2009-04-24
Your thread subject line is probably why people aren't responding, it's too vague.

Have you tried goofing around with "alsamixer" at the command line?

According to the help text from ```
alsactl --help
```

the default config file, at least for 9.04 is stored at /var/lib/alsa/asound.state - maybe there's something helpful in there?

If you can figure out the kernel module used for your integrated sound, you could just add that module to the blacklist. That's not a very graceful solution, but it should work.

---

