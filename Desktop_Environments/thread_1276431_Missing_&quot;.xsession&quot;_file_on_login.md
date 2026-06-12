---
title: "Missing &quot;.xsession&quot; file on login"
date: 2009-09-27
forum: Desktop Environments
---

### Post by glubbdrubb on 2009-09-27
This is the message I get when I try to login:

```
/etc/gdm/Xsession: Beginning session setup...
Xsession: unable to start X session --- no "/home/victor/.xsession" file, no 
"/home/victor/.Xsession" file, no session managers, no window managers, and no 
terminal emulators found; aborting.
```

I now have to sign in using "Failsafe Gnome" which works but it is a hassle.

I have set Ubuntu to login to my account automatically so every time I restart Ubuntu I get that meesage.

Please help.

---

### Post by wojox on 2009-09-27
Is your Xsession file missing? Go into /etc/gdm and look for Xsession.

---

### Post by renkinjutsu on 2009-09-27
that's odd.. i don't have an .Xsession file in my home directory at all..

maybe you have to tweak the the Xsession script in /etc/X11 to execute gnome-session instead of ~/.Xsession

---

### Post by glubbdrubb on 2009-09-27
Well, it is not in my home directory. I have not checked /etc/gdm yet(and can't, for the moment.

I forgot to mention that this all started becausae there was a power cut when the PC had been suspended.

Edit: renkinjutsu, I did not see your post when I posted mine. Please explain what you mean.

---

### Post by wojox on 2009-09-27
I don't have one in my home directory either. I looked in /etc/gdm and there is one that should load.

---

### Post by glubbdrubb on 2009-09-27
Well, I will have to check /etc/gdm when I get home tonight.
What should I do if find it? And if I don't?

---

### Post by glubbdrubb on 2009-09-29
Well, I found it in /etc/gdm so I simply copied it to my home directory and voila it boots with out a problem.... mostly.
It now hangs for about two seconds where I see my mouse but not my desktop.
Wierd

---

