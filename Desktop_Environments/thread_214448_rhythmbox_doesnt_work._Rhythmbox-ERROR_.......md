---
title: "rhythmbox doesnt work. Rhythmbox-ERROR **......"
date: 2006-07-12
forum: Desktop Environments
---

### Post by nismoskys on 2006-07-12
well i've been using Banshee for a while but needed to go back into rhythmbox (0.9.4.1) for some things and have discovered its not working anymore. im not sure but i Think this is since i upgraded to dapper. i've tried reinstalling it but i get the same problem.

whenever i start it up, i see the main window with all my songs listed, but before i can click inside i get "The application Rhythmbox has quit unexpectedly"

trying from the terminal i get...
```
jaanisar@jaanisar:~$ rhythmbox

(rhythmbox:7921): Rhythmbox-WARNING **: Unable to start mDNS browsing: MDNS service is not running

Rhythmbox-ERROR **: file rb-entry-view.c: line 1921 (rb_entry_view_resort_model): assertion failed: (sort_data)
aborting...
jaanisar@jaanisar:~$
```

anyone know why?

btw the deb im using was created by Loic Minier <lool@dooz.org>

---

