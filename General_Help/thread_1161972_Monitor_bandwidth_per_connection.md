---
title: "Monitor bandwidth per connection"
date: 2009-05-17
forum: General Help
---

### Post by sv1cdn on 2009-05-17
Wanted to share my discoveries.
Been looking for a program that will show me the active network connections and the bandwidth used per connection.
Don't look any more, try IFTOP package. Install it from package manager. Open a terminal and type:
> sudo iftop -i interface
where interface is the name of your network interface. Could also be a wireless one! If you don't know, then simply try:
> sudo iftop
More details in man iftop
:D

---

### Post by jetpeach on 2009-12-14
thanks! i was trying to decipher the output of netstat, this is better!

---

### Post by hakermania on 2009-12-27
Yeah, ok but if I want to restrict my up and down speed?

---

