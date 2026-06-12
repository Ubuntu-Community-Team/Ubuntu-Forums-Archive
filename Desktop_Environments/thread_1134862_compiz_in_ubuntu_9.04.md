---
title: "compiz in ubuntu 9.04"
date: 2009-04-24
forum: Desktop Environments
---

### Post by andrea000 on 2009-04-24
my nvidia driver is black listed in 8.10 
will this still be the case in 9.04 and 
is there a work around for it?

---

### Post by b-boy on 2009-04-24
I would not be suprised if it is still black listed. My Intel card was working fine in 8.10 now in jaunty its does not even work at all and it is also black listed

---

### Post by MeanEYE on 2009-04-24
Quick and dirty workaround:

gksu gedit /usr/bin/compiz

Line 64 contains blacklisted cards. As far as I see there is no nvidia in it but still that's the place to look... If you find your graphic card there just comment the line by placing # on the begining... save and restart compiz (or log out/in)...

---

### Post by Zabadda on 2009-04-24
i found mine on the list T="$T 8086:2a02 " # Intel GM965 what do u mean place a comment? im a n00b on this sorry

---

### Post by pbeesley on 2009-04-24
to comment out a line simply put a # in front of it.....for example

T="$T 8086:2a02 " # Intel GM965

would become

# T="$T 8086:2a02 " # Intel GM965

---

### Post by Zabadda on 2009-04-24
thats awesome thank you guys :) all my effects are back and working'

---

### Post by andrea000 on 2009-04-24
Thank you all for the work around
i'm running 8.10 but i think i am
going to upgrade sooner then i do
most of the time.I had problems
out of 8.10 so i went back to 8.04
and it took me a year to upgrade
back to 8.10.

---

