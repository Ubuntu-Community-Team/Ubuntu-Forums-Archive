---
title: "I've just installed Hoary"
date: 2005-03-29
forum: Desktop Environments
---

### Post by CouchMaster on 2005-03-29
and I'm very impressed, but I've got two questions.
1. How do you look for, and install patches and updates?  I can't seem to find a service in Hoary that does this.
2. My screen savers just flat don't work. I can't even preview them, and if I hi-lite one and set it to come on in 2 minutes or so - nothing happens, except the clock freezes and the cursor vanishes when it's time for the screen saver to come on.
As you can tell I'm a NoOB so any help at all is welcome.

---

### Post by oracledarren on 2005-03-29
Are you logged in as root ?

The reason I ask is for security the root user will now have an enabled screensaver, although like you say you can still preview them.  :smile:

---

### Post by localzuk on 2005-03-29
The tool is a little icon in the top right of the screen, called 'Update Manager'.

Else in a terminal type:

sudo apt-get dist-upgrade upgrade

Which should do the same thing.

---

### Post by lucaramel on 2005-03-29
Actually, I've upgraded my Hoary installation yesterday, and this little icon does not appear anymore...
Does anyone know why ?

EDIT : OK, nevermind, the icon just disappears when there's no update available :)

---

