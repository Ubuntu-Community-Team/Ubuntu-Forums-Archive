---
title: "Why can't I listen to sound from Amarok and the internet at the same time?"
date: 2009-01-07
forum: General Help
---

### Post by bobleny on 2009-01-07
Why can't I listen to sound from Amarok and the internet at the same time?

Hi, I'm having the exact same issue as I had before....
[http://ubuntuforums.org/showthread.php?t=538157](http://ubuntuforums.org/showthread.php?t=538157)

The solution was simple, I simply need to edit a file: /etc/firefox/firefoxrc
and install a program: alsa-oss

Worked like a charm!

The problem now is, that file doesn't exist! I even ran a search on the whole system for "firefoxrc". Nothing was found.

Does any one have any ideas?

Thanks!

Oh yes, I am running Kubuntu 8.04.

---

### Post by bobleny on 2009-01-09
What, it can't be that difficult can it!?????

---

### Post by mssever on 2009-01-09
If you were running Ubuntu, I'd refer you to [this thread]("http://ubuntuforums.org/showthread.php?t=789578"), since it sounds like a PulseAudio. I don't know whether Kubuntu uses PulseAudio, so I thought I'd point you to that thread just in case.

---

