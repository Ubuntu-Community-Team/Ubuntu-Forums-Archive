---
title: "[PLEASE ANSWER]Gnomad2 issues"
date: 2006-01-06
forum: General Help
---

### Post by simplyw00x on 2006-01-06
I have installed the latest Gnomad2 with the latest libnjb and it runs fine. When connecting to my njb2, however, the message 
```
LIBNJB Panic: njb3_ping returned status code 0002!
```
appears in the terminal window. After a few seconds I get:
```
Could not open jukebox:
njb3_ping: bad status from Jukebox
usb_control_msg: error sending control message: Connection timed out
```
as an error in the program. Clicking 'Jukebox Library'/'Rescan contents' produces:
```
Could not open jukebox:
usb_claim_interface: Device or resource busy
```
Unplugging the JB (it has the 'files busy' icon) and then pluggin it in again and trying the 'Rescan contents' again nearly crashes my computer, gives the ping error in the terminal again and then the usb_control_msg again.

SOMEBODY HELP!

[EDIT] This also happens with The repo versions of gnomad2 and libnjb

---

### Post by sciurus on 2006-01-06
I used the version in the repositores recently with my Nomad Jukebox 1 with no problem. Have you tried Neutrino?

---

### Post by simplyw00x on 2006-01-08
Doesn't work either, neither does Banshee.

---

### Post by dregin on 2007-05-01
Hey, I'm getting this same error with a zen micro. Did you manage to resolve your problem?

---

### Post by simplyw00x on 2007-05-17
Sadly not. I solved it by eventually getting a different mp3 player...

---

