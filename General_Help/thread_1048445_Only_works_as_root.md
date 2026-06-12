---
title: "Only works as root"
date: 2009-01-23
forum: General Help
---

### Post by roberto.eiberle on 2009-01-23
I repaired a broken Intrepid copying over the /etc file from a new install. Now everything works except for the fact that I have to launch all applications that use some sort of device e.g. Kaffeine with dvb as root from the terminal, otherwise I get access denied. Some idea how to remedy ?

---

### Post by ByteJuggler on 2009-01-23
Off the cuff: Compare the permissions and ownerships in /dev/* with those from a new install and repair as neccesary with "chmod" and "chown"

---

### Post by roberto.eiberle on 2009-01-23
that was it, thank you!

---

### Post by ByteJuggler on 2009-01-25
> **roberto.eiberle said:**
> that was it, thank you!

My pleasure!  ;)  Very pleased my guess was right! :p

---

