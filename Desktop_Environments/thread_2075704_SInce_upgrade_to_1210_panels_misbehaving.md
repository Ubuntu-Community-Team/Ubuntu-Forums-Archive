---
title: "SInce upgrade to 12:10 panels misbehaving"
date: 2012-10-24
forum: Desktop Environments
---

### Post by Jonners59 on 2012-10-24
I have upgraded my PC from 12:04 to 12:10 and have some issues with the panels.

I have one panel that the icons have gone huge and when I try and shrink the panel the icons stay the same size and just get squashed together.

I also find the panels do not always appear.

The Unity panel and launcher are still there, but I would like to disable them.

Any ideas.

---

### Post by Sean Dewlin on 2012-10-24
I had some issues with panels after upgrade too. You can disable panels that you don't need by right-clicking them (either click "remove" or "panel preferences"). Also, enabling display composing solved lots of problems with icons for me.

---

### Post by Jonners59 on 2012-10-25
Yes, did all that.  I created a new panel and re added, but left out the Windows icons, they don't seem to resize.  Sorted now.

> **Sean Dewlin said:**
> enabling display composing solved lots of problems with icons for me.

That might be interesting to try...

---

### Post by Jonners59 on 2012-10-27
> **Sean Dewlin said:**
> Also, enabling display composing

Where did you find this option, please?

---

### Post by Jonners59 on 2012-10-28
I can not shut down one of my machines....  A 64-bit PC does not have the shutdown or restart option in the "Action Button".  The options are ticked in the "Properties", but they are greyed out and unavailable.

Everything seems to be the same as the other two machines I have updated from 12:04 to 12:10.

Any help, please?

_**A temporary fix:**_
I created a Launcher in my panel and added the command:
```
terminator -e "sudo shutdown -h now"
```
And named it Shutdown with a nice ICON

Terminator was installed via Ubuntu Software Centre.....

---

