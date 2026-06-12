---
title: "Firefox Issues"
date: 2006-03-30
forum: Desktop Environments
---

### Post by ph8 on 2006-03-30
Hi all,

I've installed firefox from scratch (package) and I don't appear to be able to add extensions, whenever i click an extension link (e.g. from addons.mozilla.org) the 'install/cancel' box appears, i click install and the extensions window just opens (nothing else happens).

Anyone know how to fix this?

Henri

---

### Post by gregbzh on 2006-03-30
I'm in the same boat.  I've tried installing 3 or 4 extensions tonight and the same thing happens.  Any ideas?

---

### Post by ph8 on 2006-03-31
Just keeping this thread alive, it looks like this is a package problem - can anyone let us know how to fix it?

---

### Post by ph8 on 2006-04-06
Alert! Helpless newbies! Anyone?](*,)

---

### Post by towsonu2003 on 2006-04-06
[QUOTE=ph8]
I've installed firefox from scratch (package) [/QUOTE]
package... do you mean you got it from the repos or from mozilla? anyway, close firefox, move your firefox folder, and restart firefox in terminal: 
```

mv ~/.mozilla/firefox ~/.mozilla/firefox.broken
firefox
``` any errors, pls copy paste here.

---

### Post by ph8 on 2006-04-17
[QUOTE=towsonu2003]package... do you mean you got it from the repos or from mozilla? anyway, close firefox, move your firefox folder, and restart firefox in terminal: 
```

mv ~/.mozilla/firefox ~/.mozilla/firefox.broken
firefox
``` any errors, pls copy paste here.[/QUOTE]

Same problem, no errors were displayed in console, I got it from the repos - surprised more people aren't having the same problem!

---

### Post by ph8 on 2006-04-17
Apparently the standard repos firefox version has issues that no one's bothered to fix, the IRC channel referred me to this link:
[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

---

### Post by towsonu2003 on 2006-04-17
pls file a bug report: [https://launchpad.net/distros/ubuntu/+bugs](https://launchpad.net/distros/ubuntu/+bugs)

> 
Apparently the standard repos firefox version has issues that no one's bothered to fix
yes, that is correct.

---

### Post by glotz on 2006-04-30
And besides some issues, vulnerabilities are found all the time, so it really is a good idea to upgrade. Wasn't too hard. See [http://www.mozilla.org/projects/security/known-vulnerabilities.html#Firefox](http://www.mozilla.org/projects/security/known-vulnerabilities.html#Firefox)

---

