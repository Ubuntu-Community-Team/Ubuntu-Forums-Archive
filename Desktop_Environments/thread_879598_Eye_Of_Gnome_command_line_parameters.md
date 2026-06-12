---
title: "Eye Of Gnome command line parameters"
date: 2008-08-04
forum: Desktop Environments
---

### Post by nagylzs on 2008-08-04
Hi All,

I need often need to print images with the following settings:

- load the image in eog (eye of gnome)
- set print destination to a different printer
- set source of paper from "manual feed slot" to "tray"
- change print width to 90mm
- change print margin to 32/32 mm

My question is: how can I automate this? This should NOT be the default setting for eog, because I often print other types of images and my default setting are just fine for that. Is it possible to save a custom configuration and use that for "eog" in certain cases? I'm dreaming about a command line option that tells eog what configuration to use. Unfortunately, I see that there is the "--sm-config-prefix" option but not sure how to use it. There is no "save configuration as" dialog in eog. Also my required settings are in the "print..." dialog and I'm not sure if that is part of the configuration. If this cannot be done with eof, what other options I have?

Thank you.

---

### Post by astex on 2011-05-12
look in:

$ man lpr

---

### Post by domino1241 on 2013-01-18
I would also like to know how to print images from the command line instead of opening eog and printing from there.

Typing 'man lpr' and searching 'image', 'jpg' or 'png' or the like doesn't return anything.  Same with eog and

---

### Post by oldos2er on 2013-01-18
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

