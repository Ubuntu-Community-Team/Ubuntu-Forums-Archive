---
title: "Can only log on in GNOME Failsafe mode"
date: 2009-04-10
forum: General Help
---

### Post by Danger Fox on 2009-04-10
I recently removed pulse audio in order to configure my sound and I finally got it working, but when I logged out and tried to log back in I got an error telling me to try failsafe mode. When I log in under GNOME Failsafe everything is fine, but I can't seem to find a solution to this. When I view details of the log in error, the file that is causing the problem seems to be this: "Couldn't exec /usr/bin/pulse-session: no such file directory." If anyone else has got this error and fixed it please let me know how, or if anyone can point me in the right direction to get this fixed would be great too.

---

### Post by pbpersson on 2009-04-10
So, is the file in question there?  Can you see it?  Is it set to executable?

The file on my machine is a shell script and this is what is contained inside it:

```
#!/bin/sh

# Wrapper script to load pulseaudio at X session starttttttttttttt, when GNOME
# is chosen as the desktop environment.

/usr/bin/pulseaudio -D --log-target=syslog

exec "$@"
```

---

### Post by Danger Fox on 2009-04-10
The file does not exist on my computer. Do you think that making this file would fix the problem?

---

### Post by Danger Fox on 2009-04-10
Scratch that idea, all it did was give me a slightly different error message replacing "no such file directory" with "Permission denied"

---

### Post by Danger Fox on 2009-04-11
Yay, I solved the problem. What I needed to do was create the file and then set it as an executable. Thanks for the help by giving me the script.

---

