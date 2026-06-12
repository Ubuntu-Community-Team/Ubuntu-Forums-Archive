---
title: "Initializing sound output drivers - segmentation fault with pidgin"
date: 2009-04-06
forum: General Help
---

### Post by PaulWhipp on 2009-04-06
Following the last round of 8.10 updates, Pidgin no longer works for me.

Running it with debug yields
```

...
(19:38:05) stun: using server 
(19:38:05) sound: Initializing sound output drivers.
Segmentation fault

```

"lspci | grep audio" does not return anything. I'm not really sure if it should but another 2007 forum post said it should.

How can I check and reinstall the necessary sound stuff?

I get sound when I boot (the usual drum roll etc.) but then apps like rhythm and pidgin (and gnome-settings-daemon) are all failing to run.

---

### Post by Sam Lars on 2009-04-07
Can you go into your sound properties in the System menu and see if you can get the tests to work?

---

### Post by PaulWhipp on 2009-04-07
No. If I click on the sounds menu options I get the waiting cursor for a bit and then nothing -
```

~ $ gnome-sound-properties
Error re-scanning registry , child terminated by signal
Run 'gnome-sound-properties --help' to see a full list of available command line options.


```

---

