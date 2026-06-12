---
title: "Terminal closes immediately upon opening"
date: 2011-02-09
forum: Desktop Environments
---

### Post by shouse on 2011-02-09
I really can't say what I did that may have triggered this problem.  I've been trying to setup remote access through SSH but that's about it.  Haven't changed any settings in a bit though.  I downloaded Konsole and it closes immediately as well.  IDeas?

---

### Post by papibe on 2011-02-10
Is it just when you ssh? Does it happen when you open a gnome-terminal (local graphical terminal)?

Here's a similar [thread]("http://ubuntuforums.org/showthread.php?t=1578473").

Regards.

---

### Post by shouse on 2011-02-10
happens regardless of ssh. Happens on multiple users.  I'm pretty sure the application is labeled as just gnome-terminal.

I've only been messing around with linux for a couple weeks and have already found a way to break it,....I'm pretty good right ;)

---

### Post by gmargo on 2011-02-10
Here's a trick to force a different shell instead of bash.  Hit Alt-F2 to bring up the run dialog, and enter
```

env SHELL=/bin/sh gnome-terminal

```Hopefully that will at least get a window open so you can search for the problem.

---

### Post by shouse on 2011-02-10
ok yea that got it working at least.  So ideas what I should start looking for?

---

### Post by Copper Bezel on 2011-02-11
Sorry, posted, then answered my own question. So weird.

---

### Post by papibe on 2011-02-11
Have you customized your .bashrc? If so maybe there's the problem. Recover the last backup of that file or undo your changes.

After that, my guess would be on the completion scripts. If you installed recently any software that uses a new "extension" for files, it have also may have installed a completion script (for example, if you install unrar, as a result you'll have a unrar completion script added to /etc/bash_completion.d).

Although helpful, some of those scripts do not work well in a non standard installation (different system paths for example).

BTW, since you maybe running sh on your gnome-terminal as suggested by gmargo, you can call bash like this:
```
$ bash
```
that way you can test if it's working or not.

Regards.

---

