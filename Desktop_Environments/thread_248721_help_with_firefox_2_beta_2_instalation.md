---
title: "help with firefox 2 beta 2 instalation"
date: 2006-09-01
forum: Desktop Environments
---

### Post by searayman on 2006-09-01
i downloaded the firefox 2 beta 2 and extracted it and have a file called firefox, now how do i launch firefox 2 beta 2?

---

### Post by llamakc on 2006-09-01
./firefox-installer

---

### Post by sabitha on 2006-09-01
or u can just run with /home/username/firefox/firefox

---

### Post by searayman on 2006-09-01
dont i need to compile it first?

---

### Post by Rui Pais on 2006-09-01
> **searayman said:**
> dont i need to compile it first?

No if you download a binary from somewhere like here:
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/2.0b2-candidates/rc2/]("http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/2.0b2-candidates/rc2/")

btw, this late beta2 is amazing. 
Fast, very stable and very eyecandy... the new 'corrector as you write' is soooo useful in a forum for non-english users... 
This promise a great 2 version!!!

---

### Post by kerry_s on 2006-09-01
You could just copy it to /usr/lib , you have to rename the old firefox to firefox.old then just copy the new one there. Don't forget to copy the plugins as well(you have to be root: sudo nautilus /usr/lib). It's simple drag and drop or copy and paste, but if you decide to go back to the old one you just delete the new firefox folder and rename the old one back to just firefox. I find this way much safer and you have a backup just in case.

---

### Post by llamakc on 2006-09-01
If you want it to be available for just yourself, leave it in /home/username. If you want other users to have access to it, put it in /opt or /usr/local.

---

### Post by hellfried on 2006-09-01
> **llamakc said:**
> If you want it to be available for just yourself, leave it in /home/username. If you want other users to have access to it, put it in /opt or /usr/local.

just downloaded 2.0b2 and love it except for the fact that the live ip extension does not work anymore. any other alternatives?


updated:
sorted the problem out by installing the nightly tester tool extension and forcing compatibility of the live ip extension.

anyhow now i noticed that java is not working in this version of firefox. is pointers?

---

