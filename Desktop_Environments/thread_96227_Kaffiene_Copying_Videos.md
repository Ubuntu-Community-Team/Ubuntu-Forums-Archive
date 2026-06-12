---
title: "Kaffiene Copying Videos"
date: 2005-11-28
forum: Desktop Environments
---

### Post by JShadow on 2005-11-28
After a recent update my kaffiene started to copy video files to /tmp before playing them. It can take a while sometimes and is pretty irritating.

I'm using the Xine engine. Any idea what might be causing this behavior?

---

### Post by Alex_Perry on 2005-11-28
It sounds like you're using KDE 3.5 and opening your files from home:/ (the kio_slave) and not /home/user. When you open a file from the kio_slave, it copies the file to /tmp. 

One thing I've done to avoid this is open kaffeine, then drag the file into the playlist, then play it. It doesn't copy the file into /tmp before playing that way.

---

### Post by JShadow on 2005-11-28
Ah, that clears things up a little. Is there a reason it gets copied this way or is this a bug?

---

### Post by Alex_Perry on 2005-11-28
I don't know if it's a bug. Never taken the time to look for/file one.

---

### Post by vh1 on 2005-11-29
I noticed (a while ago) that kaffeine used to complain when trying to play a file that wasn't "local". I guess it copies them to /tmp instead of complaining now. I don't really like this behaviour

---

### Post by daller on 2005-12-13
Hi There, I've made a workaround for the KDE3.5 fileassociations:

Fix all KDE-applications with this command:

```

sudo perl -pi -e 's|%U|\%f|g' /usr/share/applications/kde/*.desktop

```

Anybody interested, This fixes OpenOffice2.0:

```

sudo perl -pi -e 's|%U|\%f|g' /usr/share/applications/ooo2-*.desktop

```

WARNING: This is a crappy homemade workaround - But it works!

---

