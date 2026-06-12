---
title: "Possible security bug found with screensaver password"
date: 2005-05-03
forum: Desktop Environments
---

### Post by intendedaccel on 2005-05-03
Hello, I'm wondering if anybody else has this problem. When I leave my desk I always lock my screen. When I come back and type my password it appears to type the same text into whatever program that last had focus before you left. 

For example, I use xChat for IRC. When this happens, I see that my password has been posted to whatever IRC channel I am in. 

Is there a fix for this? I think this could be a huge issue!

Thank you!

---

### Post by shakin on 2005-05-03
I don't have this issue. I just tested with gedit the last focused app. Can you replicate this problem with multiple apps, like gedit, openoffice, firefox, etc?

---

### Post by intendedaccel on 2005-05-03
[QUOTE=shakin]I don't have this issue. I just tested with gedit the last focused app. Can you replicate this problem with multiple apps, like gedit, openoffice, firefox, etc?[/QUOTE]

I've only noticed the problem with Xchat, so maybe it's specific to that. It has happened several times though so it wasn't a fluke thing.

---

### Post by shakin on 2005-05-03
[QUOTE=intendedaccel]I've only noticed the problem with Xchat, so maybe it's specific to that. It has happened several times though so it wasn't a fluke thing.[/QUOTE]

XChat may have a nonstandard method for polling keystrokes. It detects that it still has focus and just captures everything typed.

---

### Post by intendedaccel on 2005-05-03
I've just tested it again, and I can't reliably make it happen. It has happened more than once though. I'll try to see if I can narrow it down further.

---

### Post by intendedaccel on 2005-05-05
[QUOTE=shakin]XChat may have a nonstandard method for polling keystrokes. It detects that it still has focus and just captures everything typed.[/QUOTE]
 Today this happened twice with the terminal services client. It is not limited to xchat.

---

### Post by 23meg on 2005-05-05
hmm, i can't replicate this with xchat. are you using the version of xchat that's supplied with Hoary?

---

### Post by dewey on 2005-05-05
I've never had this problem, on any linux distro.  Odd.

Have you installed any applications possibly untrustworthy lately?  Someone may have modified your screensaver lock to cleartext?

---

### Post by 23meg on 2005-05-05
i've tried it with tsc, and many other apps, and still can't replicate. are you running as a normal user when this happens?

---

### Post by intendedaccel on 2005-05-06
[QUOTE=23meg]hmm, i can't replicate this with xchat. are you using the version of xchat that's supplied with Hoary?[/QUOTE]
 Yes, version that ships with hoary.

---

### Post by intendedaccel on 2005-05-06
[QUOTE=dewey]I've never had this problem, on any linux distro.  Odd.

Have you installed any applications possibly untrustworthy lately?  Someone may have modified your screensaver lock to cleartext?[/QUOTE]
 Nope, just a default ubuntu install.

---

### Post by intendedaccel on 2005-05-06
[QUOTE=23meg]i've tried it with tsc, and many other apps, and still can't replicate. are you running as a normal user when this happens?[/QUOTE]
 Yes, a normal user.

---

