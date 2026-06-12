---
title: "default desktop environment"
date: 2011-09-07
forum: Desktop Environments
---

### Post by jopeto on 2011-09-07
When I log onto Ubuntu, gdm always remembers my last desktop environment under sessions. Is there any way to make a specific desktop environment default, no matter which one I've used the last time?

For example, I like using FVWM, however other people using the same computer freak out whenever they see something different from Gnome (and I've set up the computer in such a way that it doesn't need a password, so it automatically bypasses the gdm login screen on start up). Is there a way to make Gnome always default on start-up no matter whether I've used FVWM in my previous session?

Thanks in advance.

---

### Post by raja.genupula on 2011-09-07
system settings --> login screen 
there you can choose what ever the session you always want i mean as default .  

all the best .

---

### Post by jopeto on 2011-09-07
Hi raja,

Thanks a lot for your reply. However that doesn't really seem to work. Even if I have Gnome selected, after I log onto FVWM and restart, I get back into FVWM...

---

### Post by raja.genupula on 2011-09-07
ok you said as last session ....
ok try this , after selecting a  different session  is it asking for save session for next login or anything else .(in fedora we have some thing like this )

---

### Post by gldvorak on 2011-09-07
Goto Systen Settings; Startup & Shutdown; Session Management; On Login -- select Manually saved session. But, I have never manually saved a session, so I cannot help you there.

---

### Post by Krytarik on 2011-09-07
GDM relies on the file "/var/cache/gdm/USERNAME/dmrc" to set the login options, always. Eventually, upon logging you in, it updates the - similar - file "~/.dmrc" in your home directory, and then updates its copy with it, therefore copying it.

But it can't do this if you remove the write permission from its file, thus leaving the session settings stored within it untouched until you re-enable the write permission again, or modify it via root access.

So, what you need to do is log in to your desired default session, and then remove the write permission with a command like this:
```
chmod 444 /var/cache/gdm/USERNAME/dmrc
```To re-enable the write permission again, run a command like this:
```
chmod 644 /var/cache/gdm/USERNAME/dmrc
```Of course, you can also do this through the right-click menu of Nautilus if you like.

Greetings.

---

### Post by jopeto on 2011-09-08
raja - no, in ubuntu I guess it doesn't ask you to save the last session.
gldvorak - I didn't try your solution, but maybe it would work.
Krytarik - that did the trick! I was trying to find a solution for it for several days!

Thanks a lot to everyone who helped out!

---

