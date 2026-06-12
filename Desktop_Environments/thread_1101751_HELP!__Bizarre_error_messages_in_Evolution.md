---
title: "HELP!  Bizarre error messages in Evolution"
date: 2009-03-20
forum: Desktop Environments
---

### Post by The Rocker on 2009-03-20
Hey all,

Evolution just suddenly locked up and quit working.  I forced quit, tried to restart and it never came up.  Then I rebooted the computer entirely, still the same thing.

So I tried to run it from a terminal and I got some very strange error messages:

```
(evolution:8163): camel-WARNING **: Could not find key entry for word 'w000000000': Success


(evolution:8163): camel-WARNING **: Could not find key entry for word 'yeahhhhhhhhhhhh': Success


(evolution:8163): camel-WARNING **: Could not find key entry for word 'w00000000000000': Success


(evolution:8163): camel-WARNING **: Could not find key entry for word 'yahhhhhhhhhhhhhh': Success


(evolution:8163): camel-WARNING **: Could not find key entry for word 'w00000000000000000000': Success


(evolution:8163): camel-WARNING **: Could not find key entry for word 'yeahhhhhhhhh': Success


(evolution:8163): camel-WARNING **: Could not find key entry for word 'w0000000000000000t': Success


(evolution:8163): camel-WARNING **: Could not find key entry for word 'yeahhhhhhhhhh': Success


(evolution:8163): camel-WARNING **: Could not find key entry for word '72am22e3o9w52xha1012000003o9w0mpa': Success


(evolution:8163): camel-WARNING **: Could not find key entry for word '72am22e3ol652xha1012000003ol60mpa': Success


(evolution:8163): camel-WARNING **: Could not find key entry for word 'olaof00020000000970': Success

```

It goes on and on, mostly with strings of gibberish for the entries that it can't find.  However, the first few messages "w00000000" "Yeaahhhhhhh" etc. almost look like it's a virus or something, no?

I tried deleting all my index files and anything else that wasn't a mail file from the .evolution/mail/local directory.  Same result.

Any other ideas?

---

### Post by The Rocker on 2009-03-20
UPDATE: If I wait long enough, it eventually comes up in offline mode.  It seems to have rebuilt the indexes.  Now, however, it's stuck fetching mail when I try to go back online.

GRRRR.

---

