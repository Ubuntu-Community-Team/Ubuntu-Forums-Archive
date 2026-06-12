---
title: "Can I start a process so it's output goes to a virtual terminal?"
date: 2009-01-19
forum: General Help
---

### Post by paul2110 on 2009-01-19
Hi there,

I have Ubuntu Server 6.06.1 running Asterisk PBX and a custom Java application.

Both Asterisk and the Java app are started in /etc/inittab on run level 2 so they're both running once Ubuntu has booted up.

However, both apps send very verbose information to the main console and I was wondering if it's possible to start each process in a separate terminal so I can switch to the terminals to see the console output (using Ctrl+Alt+F1, F2 etc.)  For example I could start Asterisk in Terminal #2 and the Java app in Terminal #3...

Is there any way to do this using either inittab or a standard script?

---

### Post by paul2110 on 2009-01-19
Anyone? :)

---

### Post by dcstar on 2009-01-20
> **paul2110 said:**
> Hi there,

I have Ubuntu Server 6.06.1 running Asterisk PBX and a custom Java application.

Both Asterisk and the Java app are started in /etc/inittab on run level 2 so they're both running once Ubuntu has booted up.

However, both apps send very verbose information to the main console and I was wondering if it's possible to start each process in a separate terminal so I can switch to the terminals to see the console output (using Ctrl+Alt+F1, F2 etc.)  For example I could start Asterisk in Terminal #2 and the Java app in Terminal #3...

Is there any way to do this using either inittab or a standard script?

Each of these is a /dev/tty (as you see when you CTRL-ALT-Fn to one of them) , so pick the one you want to use and send the output there (as /dev/tty8 has the system startup stuff).

---

### Post by paul2110 on 2009-01-20
> **dcstar said:**
> Each of these is a /dev/tty (as you see when you CTRL-ALT-Fn to one of them) , so pick the one you want to use and send the output there (as /dev/tty8 has the system startup stuff).

Thanks:D, but I'm still a bit of a noob, so could you explain exactly how I'd do this?  eg. what do I write in which file?

---

### Post by snova on 2009-01-20
/dev/tty1, tty2, tty3, etc., are special files representing their respective terminals. They can be written to just as any file, but anything you write to them will show up on a terminal.

So, something like this:

```
**command** >/dev/tty2
```

Then you can switch to Ctrl-Alt-F2 (in this case) and see the messages.

However, this will only redirect standard output, not error messages. To redirect both:

```
**command** &>/dev/tty2
```

---

### Post by paul2110 on 2009-01-21
Thanks! :D

---

