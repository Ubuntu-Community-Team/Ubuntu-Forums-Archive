---
title: "Error with storYBook on start"
date: 2010-01-08
forum: Education &amp; Science
---

### Post by Tmatherne on 2010-01-08
I am using this software for a Creative Writing elective, so I hope it is OK that I put this in Education...  I guess I'll know if it gets moved.

I am using a software called [storYBook]("http://storybook.intertec.ch/") and it was working fine in early December, right before Christmas.  I started it up again yesterday, and when I typed the startup command into the terminal, was greeted by these error messages:

```
tommie@tommie-laptop:/media/D6C6C0E3C6C0C4C9/misc/storybook_2.1.12_linux$ ./storybook.sh
starting ...
Exception during event dispatch:
java.lang.NullPointerException
   at ch.intertec.storybook.StorybookApp.init(Unknown Source)
   at ch.intertec.storybook.StorybookApp.access$000(Unknown Source)
   at ch.intertec.storybook.StorybookApp$1.run(Unknown Source)
   at java.awt.event.InvocationEvent.dispatch(libgcj.so.10)
   at java.awt.EventQueue.dispatchEvent(libgcj.so.10)
   at java.awt.EventDispatchThread.run(libgcj.so.10)
done.

```

I have done nothing to change my system other than normal updates from Update Manager.  Anyone got an idea why this is happening?  I'm not exactly familiar enough with Java runtimes to know what the issue is here.

Thanks for any help.

Tommie Matherne

---

### Post by katejones on 2010-03-10
I just installed storyBook and I can't get it to run either.
(I thought I was doing something wrong since I'm new to Ubuntu/Terminal..)

This is the error I get.
> username@macje:~/storybook$ ./storybook.sh
starting ...
./storybook.sh: line 4: java: command not found
done.


Did you ever get it to run?

---

### Post by Tmatherne on 2010-05-22
I just downloaded version 2.1.13 after purging the older version and reinstalling the JRE, ran the install.sh script then the storybook.sh script, and it started with no problem.  Looks like JulNoWriMo is ONNNN!

Tommie Matherne

---

