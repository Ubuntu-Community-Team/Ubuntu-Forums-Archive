---
title: "Firefox mail problems"
date: 2009-05-05
forum: General Help
---

### Post by stardustdk on 2009-05-05
Hey.

When i used to mail via Firefox in 8.04, I managed to edit the "preferred programs" so I could send via firefox, when I found maillinks on a website.

Wroted:

> firefox gmail.com 

and everything worked like a charm.

In 9.04

I use the same costum tag, but ending in the inbox of Gmail and without the maillink??

Any ideas?

Best regards

Stardustdk

---

### Post by soro2005 on 2009-05-05
something like
```
firefox gmail.com %s
```
perhaps? No idea, but seems like some variable isn't passed on.

---

### Post by stardustdk on 2009-05-05
Tried that and it produced *many* tabs and still to the inbox - not to "send mail" including the mailadress.

Best regards

Stardustdk

---

### Post by soro2005 on 2009-05-05
Something like
```
https://mail.google.com/mail/?extsrc=mailto
```
perhaps? This might work if you've set Firefox to be your default URL handler. If not, perhaps try
```
firefox https://mail.google.com/mail/?extsrc=mailto
```
Also, to populate the address field with the address from the mailto url, try
```
https://mail.google.com/mail/?extsrc=mailto&url=%s
```
or
```
firefox https://mail.google.com/mail/?extsrc=mailto&url=%s
```
Haven't tried it, though. It's from [Lifehacker](http://lifehacker.com/392287/set-firefox-3-to-launch-gmail-for-mailto-links).

---

### Post by stardustdk on 2009-05-05
The last one 

> firefox [https://mail.google.com/mail/?extsrc=mailto&url=%s](https://mail.google.com/mail/?extsrc=mailto&url=%s)

Did the trick. 
Thanx

Stardustdk

---

