---
title: "[SOLVED] Terminal command to Log Out?"
date: 2008-12-06
forum: General Help
---

### Post by scottevan on 2008-12-06
I just wrote my first python application and I need it to log the user out. Python can issue OS commands, but I can't find one that does this... I've tried "gnome-session-save --kill" but that brings up a "Log Out of Session" dialog. I need something that kills the session and requires no further confirmation from the user. 

I've also tried "killall gnome-session", but it returns "no process killed". Any advice?

Thanks!

---

### Post by scottevan on 2008-12-06
Ok, I read the documentation ("man gnome-session-save") and discovered the answer to my own question: you just need to use "--force-logout" instead of "--kill".

---

### Post by arielon on 2009-11-15
doesn't work in kubuntu.

---

### Post by dscanlonits on 2009-12-22
Hello,

I have several public machines where users sometimes connect to server volumes. Instinctively they check off the box that says remember my password. I found a terminal command to make it forget the password, but how do I disable this option all together?

Thanks.

---

### Post by shantanu18 on 2011-03-15
try this 

```

gnome-session-save --kill --silent

```

---

