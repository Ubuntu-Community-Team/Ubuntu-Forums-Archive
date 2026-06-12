---
title: "How do I install software for another release?"
date: 2009-04-10
forum: General Help
---

### Post by BobSongs on 2009-04-10
[FONT=Verdana]A package exists in the repositories called [/FONT]**[FONT=Verdana]debpartial_0+20030508.1_all.deb[/FONT]**[FONT=Verdana]. It appears in Synaptic for any release **up to** Gutsy Gibbon, but not beyond. The binary works perfectly in every release since Gutsy. From Hardy Heron and beyond, the **sources.list** file won't contain a listing to that .deb file.

Is there a way to tweak the **apt-get** command in order to force a download and installation? Or is downloading it directly from the Ubuntu repositories the only viable alternative?
[/FONT]

---

### Post by _khAttAm_ on 2009-04-10
> **BobSongs said:**
> [FONT=Verdana]Is there a way to tweak the **apt-get** command in order to force a download and installation? Or is downloading it directly from the Ubuntu repositories the only viable alternative?
[/FONT]

I think so.

---

### Post by Thura on 2009-04-10
That's what I did ...
Search for the package ... [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Then check you got the dependencies ... ( If not, download them first )
Then donwnload the file manually and use dpkg to install ....

---

### Post by BobSongs on 2009-04-11
Many thanks, one and all!

Much appreciated.

---

