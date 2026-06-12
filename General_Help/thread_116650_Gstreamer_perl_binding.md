---
title: "Gstreamer perl binding?"
date: 2006-01-13
forum: General Help
---

### Post by IdoMcFly on 2006-01-13
Hello !

I'm trying to run gmusicbrowser with gstreamer but it complains about not finding GStreamer.pm wich seems to be the perl binding to gstreamer. I can't find the package to install to get it.

Thanks for any help

---

### Post by mvaniersel on 2006-01-13
Have you tried getting the GStreamer package from CPAN?

```

perl -MCPAN -e 'shell'

...

install GStreamer

```

---

### Post by IdoMcFly on 2006-01-15
thank you for the answer. seems to be some pbl when it runs the make test though

---

### Post by IdoMcFly on 2006-01-15
i've done force install to ignore the failed tests, thank you!

---

