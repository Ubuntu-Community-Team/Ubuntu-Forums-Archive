---
title: "evolution webcal + https"
date: 2005-07-24
forum: Desktop Environments
---

### Post by fago on 2005-07-24
i've created a webdav directory which has access restrictions through http basic authentication. there i'm publishing my calendar with the help of mozilla sunbird on some windows machines.

now i want to import this calendars in evolution, but without success. 
should the evolution webcal:// url-handler work with https? 
 
if i enter a https uri in the input field - evolution substitudes it to webcal :(
i tried a uri which looks like this:
webcal://user:thepw@host/directory/file 
but evolution can't find the file (it's not available through http)

however i've already managed to publish locally created calendars with evolution on this directory.

---

### Post by dare2dreamer on 2006-01-09
How did you get evolution to publish a calendar?

---

### Post by flange on 2006-01-12
[QUOTE=fago]now i want to import this calendars in evolution, but without success. should the evolution webcal:// url-handler work with https? 
[/QUOTE]

It's a bug.  It's being fixed in the 2.5 branch.

[http://mail.gnome.org/archives/evolution-patches/2006-January/msg00001.html]("http://mail.gnome.org/archives/evolution-patches/2006-January/msg00001.html")

---

