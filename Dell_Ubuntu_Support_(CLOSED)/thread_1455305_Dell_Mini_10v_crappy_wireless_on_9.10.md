---
title: "Dell Mini 10v crappy wireless on 9.10"
date: 2010-04-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Birion on 2010-04-15
Hi,
I just got the 10v, put 9.10 UNR on it, managed to get the driver installed with the help of the ubuntumini website, and yet, for some reason, I can't see my home network at all. I can see a bunch of others (even some my other computer sitting right next to it can't see), but not the one I want. Not really sure if it helps, but iwlist scanning claims that my eth1 interface doesn't support scanning. Any help or suggestions would be much appreciated. Thanks.

---

### Post by mikewhatever on 2010-04-15
Your card should do the scanning, just run it with sudo.

sudo iwlist scan

nm-tool   #no sudo

---

### Post by Birion on 2010-04-16
And so it does. Thanks. It still doesn't see my home network (nor can it connect to it manually) 5 centimetres from the router antenna, though.

EDIT: And now that's solved. Apparently, all that was needed was resetting the router to factory settings.

---

