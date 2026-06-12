---
title: "empty serial port buffer with bash script"
date: 2009-03-28
forum: General Help
---

### Post by nunojpg on 2009-03-28
I'm using a external device via a serial port.
I want before sending any cmd to empty the serial port buffer so I know that I receive a answer to that.

This will do the trick, but it's not very efficient...:

while read -t 0 var < /dev/ttyUSB0; do continue; done


Any other solution?

---

