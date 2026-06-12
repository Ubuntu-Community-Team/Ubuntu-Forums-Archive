---
title: "Wireless on E1505"
date: 2007-07-11
forum: Dell  Ubuntu Support
---

### Post by lostinquestions on 2007-07-11
I bought the E1505 Laptop with Ubuntu the day it was released, and it's worked fine for me up until a month ago when I discovered it did not have a modem, so I could not use Dialup access. On the route to discovering that, I made lots of configuration changes -- but, alas, (and obviously) to no avail. Now, though, my wireless does not seem to be working. When I go to the network config, all I see is the (nonexistant) Modem Connection and a wired connection. For the first month that I had this, the wireless worked fine.

I tried formatting the computer, but the situation is still the same. iwconfig returns no interfaces, and the wireless hardware seems to be detected.

Any help/suggestions would be appreciated. I tried searching the forum, but couldn't find anything similar.

Thanks!
Bobby

---

### Post by Paul S on 2007-07-26
> **lostinquestions said:**
> I tried formatting the computer,

Do you mean installing the back up image?  If you haven't tried that, it would be worth a try.  Then, if it still does not work, go back to Dell for support.  They are responsible for their back up image.

HTH

---

### Post by Ek0nomik on 2007-07-26
> **lostinquestions said:**
> I bought the E1505 Laptop with Ubuntu the day it was released, and it's worked fine for me up until a month ago when I discovered it did not have a modem, so I could not use Dialup access. On the route to discovering that, I made lots of configuration changes -- but, alas, (and obviously) to no avail. Now, though, my wireless does not seem to be working. When I go to the network config, all I see is the (nonexistant) Modem Connection and a wired connection. For the first month that I had this, the wireless worked fine.

I tried formatting the computer, but the situation is still the same. iwconfig returns no interfaces, and the wireless hardware seems to be detected.

Any help/suggestions would be appreciated. I tried searching the forum, but couldn't find anything similar.

Thanks!
Bobby

What kind of wireless card is it?

If you don't know, open a terminal (Accessories/Terminal) and type in this command and post your output:

```
lspci
```

I would guess it's a 1390, but I thought those didn't work out of the box, unless Dell tweaked the install so it would.

---

