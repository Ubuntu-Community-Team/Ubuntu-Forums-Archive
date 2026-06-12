---
title: "Firestarter start up issue !!"
date: 2006-01-12
forum: Desktop Environments
---

### Post by AASZA on 2006-01-12
I have installed firestarter and I want it to run automatically on startup, I have the owner and group set to my login and i have the command gksudo /usr/sbin/firestarter in the launcher.

But on every start it says you must have root privileges to use firestarter and wont start but i can open it manually by entering my password.

Can I grant my user root privileges ?
Or is there a way around this ? or can i edit some file or something.

Help appreciated >>

I only installed Ubuntu 2 days ago and now i am using it as my main OS after getting annoyed with 2K :-) Everything Is FREE what more could you ask for ??

---

### Post by daschl on 2006-01-12
[QUOTE=AASZA]I have installed firestarter and I want it to run automatically on startup, I have the owner and group set to my login and i have the command gksudo /usr/sbin/firestarter in the launcher.

But on every start it says you must have root privileges to use firestarter and wont start but i can open it manually by entering my password.

Can I grant my user root privileges ?
Or is there a way around this ? or can i edit some file or something.

Help appreciated >>

I only installed Ubuntu 2 days ago and now i am using it as my main OS after getting annoyed with 2K :-) Everything Is FREE what more could you ask for ??[/QUOTE]

Well, you have to start it as root, so it would be nice if you dont only start it with "gksudo". install it, and then create a symlink in the /etc/rc2.d directory

```

# ln -s

```

good luck

---

### Post by AASZA on 2006-01-12
How do you create a symlink ?? 

Soz Me Noob First linux experience

---

### Post by kaamos on 2006-01-12
You can set firestarter to start up at boot in the firestarter preferences. The gui is only a tool to change the settings and to view at logs. So just choose that setting and you're good to go, no need to hassle with anything like this. :)

---

### Post by daschl on 2006-01-12
[QUOTE=kaamos]You can set firestarter to start up at boot in the firestarter preferences. The gui is only a tool to change the settings and to view at logs. So just choose that setting and you're good to go, no need to hassle with anything like this. :)[/QUOTE]

if this options is there, its better if you use this

in relation to your question:

```

$ ln -s target linkname

```

(-s for "soft", if you dont use -s you create a hard-link. for more infos run man ln)

hth

---

