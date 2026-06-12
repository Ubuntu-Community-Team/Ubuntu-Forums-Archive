---
title: "GPS alike with wifi position system project"
date: 2011-10-14
forum: Education &amp; Science
---

### Post by Dr_Lion on 2011-10-14
Hi, i dont know if this is the right place to post, if it's not feel free to change.

I'm starting a study project in university something like "wifi position system".

In a glance everything seems to be fine, but first drawback lack of money means problems coming. 
So here goes the problem, i hope you could get me any help, thanks in advance.


For my project i need to measure the "RSSI" signal in dbm or so, of a wireless network.

First question, anyone knows a good program for this? I'm trying to use kismet, but in the main screen (and i'm using text based screen without Gui) it doesn't show the noise/power, i have to press a key, "l" if i'm not wrong. The other and bigger problem, is how to log the RSSI values that i'm getting i guess 1 value peer second would be enough.

Thanks for the help.

Sorry my bad english, i'm from Portugal and i'm a bit rusty.

---

### Post by ssam on 2011-10-15
the command
```

iwlist wlan0 scan

```
might be more what you need.

if you need some data you could use [http://openbmap.org/](http://openbmap.org/)

---

