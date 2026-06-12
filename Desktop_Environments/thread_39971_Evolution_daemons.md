---
title: "Evolution daemons"
date: 2005-06-07
forum: Desktop Environments
---

### Post by kostkon on 2005-06-07
Hi

Evolution is a good program. But, as I can see in *System Monitor*, two Evolution daemons are running all the time and they use a lot of memory.

These daemons are: **evolution-alarm-notify** and **evolution-data-server-1.2**  

I don't have a state of the art pc, so, I would like to ask what these daemons do and if I can stop them running. Can I stop them without uninstalling Evolution?

Even if I have to sacrifice Evolution in order to get rid of these daemons, it's OK, I'll use Thunderbird; no big deal!

Thanks

---

### Post by jcooper on 2005-06-07
evolution-data-server is the core of evolution, and the email/contact/calendar storage for the Gnome desktop. This is a required component.

evolution-alarm-notify is a dameon which polls E-D-S for calendar / alarm events. It is responsible for the Evolution alerts.

If you use evolution, both of these are necessary. Without E-D-S, the calendar function of the clock panel applet wouldn't work, nor would any other applications that require this dameon to be running (I believe Gaim can make use of it, though does not require it).

---

