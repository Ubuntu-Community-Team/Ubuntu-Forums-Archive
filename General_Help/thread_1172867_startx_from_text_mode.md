---
title: "startx from text mode"
date: 2009-05-29
forum: General Help
---

### Post by Prelude203 on 2009-05-29
ok, heres what im trying to do (if its possible)


im loging in text mode (ctrl-alt-f4 at login screen) and then i want to manually run x from there to get to my desktop when needed but it keeps on giving me errors saying things like its already running , etc 

anyone know how to get x to start up after logging into console mode (or text mode whatever its called)


sorry im a newbie :)

---

### Post by lisati on 2009-05-29
I think you're already on to it. Does typing the following at the prompt help? ```
startx
```

---

### Post by Prelude203 on 2009-05-29
yes, startx is the command i have been doing but it just gives me a 'fatal error' basically telling me that it is already running OR sometimes it will tell me to check if there is another instance of it running , then it tells me to try and remove a temporary file and try again... i removed that temporary file and still get the same message.


am i apporching this wrong?

what im doing is:

[COLOR="DarkOrange"]
booting up

i got to the gui login screen (gdm?)

then i do ctrl alt f4 to get to console mode or 'text mode'

then login there[/COLOR]

but the problem is every once in a while i need the gui to do some things but it just wont let me start X while logged in text mode

i have to log out, exit, then login at the gdm

please any help?

---

### Post by mhgsys on 2009-05-29
why don't you just login back to gdm??
```

Ctrl+Alt+f7 

```


anyway;

the code to stop/start/=
```

sudo /etc/init.d/gdm stop

sudo /etc/init.d/gdm start

```

---

### Post by neo_1in on 2009-05-29
startx works for system only when there is no x session started automatically. As you said you get the gdm, which is an x session, hence the error. If you really want to use text system only, either use the code in the post above to stop gdm, or get rid of the display manager (gdm) itself, i.e. uninstall it.

---

### Post by Prelude203 on 2009-05-29
thanks! :p

---

### Post by Yellow Pasque on 2009-05-29
You may also be interested in bum (boot-up manager).

---

