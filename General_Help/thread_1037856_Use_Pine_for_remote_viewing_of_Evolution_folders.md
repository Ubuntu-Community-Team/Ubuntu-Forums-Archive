---
title: "Use Pine for remote viewing of Evolution folders?"
date: 2009-01-12
forum: General Help
---

### Post by knowname on 2009-01-12
Does anyone know whether it is possible to use Pine (or any other terminal based email program) to read Evolution's offline email folders? My primary computer is a desktop located in my office which I run Evolution on. When in a remote location, if I'd like to see a saved message from one of my offline folders I VNC in via a SSH connection. However, this is a little slow, the screen dimensions are funny (since my desktop monitor is so much larger than my laptop screen) and if I'm not on a linux machine I can't always do this. I'd rather just SSH in to a prompt and bring up a terminal-based program like PINE to look at my offline folders. Does anyone know if this is possible?

Thanks!

---

### Post by knowname on 2009-02-04
In case anyone else is trying this, it was a lot easier than I was making it out to be. I installed Alpine (the newer version of Pine), and within Alpine set up a new "collection", or group of mailboxes. In the settings, leave Server blank and set the path to the folder where evolution stores the offline mail. On my system, it's

```
Path      : /home/<username>/.evolution/mail/local/
```

The unfortunate thing is that alpine sees not only the mailboxes, but all the other little index files that evolution creates and keeps in the same folder. There's a "View" command within the collection setup that lets you put in a criteria for which files to show, but since all of the mailbox folders do not have an extension, there's no pattern to match for which files to include. (And as far as I can see there's no way to exclude based on a search string in alpine.)

---

