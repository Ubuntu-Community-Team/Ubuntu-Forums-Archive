---
title: "Running an application or script at startup"
date: 2010-10-13
forum: Desktop Environments
---

### Post by eeboy on 2010-10-13
I want to launch qiv upon startup to show a series of photos in slideshow fashion (this will be the sole purpose of this particular laptop). I tried adding the command via System->Preferences->Startup Applications but this does not produce the desired result. In fact, the slide show doesn't even start.

Any ideas as to how I can achieve the desired effect?

---

### Post by tk31337 on 2010-10-13
So you're trying "qiv -fst [filepath]" right?  If so, the only thing I can think of is to make sure that your filepath is defined explicitly (i.e. /home/you/Pictures/* rather than, say ~/Pictures/* or Pictures/* or something).

---

### Post by I_can_see_the_light on 2010-10-13
I'd check the man pages first, open a terminal window and enter ```
man qiv
``` and hope for the best. This way you'll see if there's any commands you can issue to the program.

---

### Post by eeboy on 2010-10-13
That is correct... I am issuing qiv [switches] [path]. The path is actually of the form ~/Pictures. This works when run directly from a terminal so I would expect it to behave the same when run as a startup application but that's not the case.

In any case, explicitly defining the path does not help in my latest test. Is it possible that something is causing the slide show to immediately exit (as if the user hit esc)? Perhaps when the very next startup application launches it causes qiv to exit? Is there a way to make qiv the last program launched? Is there a log file to reference to see if the process was even active for a moment?

Thanks!

---

### Post by I_can_see_the_light on 2010-10-14
You could try creating a bash script with a time delay before the app starts.

```
#!/bin/bash
sleep 20 && <your_command_here>;
```

---

### Post by eeboy on 2010-10-14
That did the trick... A simple 5 second delay has got me up and running. Thanks!

---

