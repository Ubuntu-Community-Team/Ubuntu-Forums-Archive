---
title: "smb.conf space question"
date: 2009-06-15
forum: General Help
---

### Post by cheddercaveman on 2009-06-15
Ok, so I'm trying to setup a samba share using smb.conf and it turns out that my path has a space in it.  I've tried several things, but none of them seem to be yielding me a share.  This seems like something that would come up fairly regularly but i can't seem to find documentation on it.  I found some documentation that said to connect a client like this...

//<server ip/name>/path/with\040space

... but that same logic doesn't seem to be working in the smb.conf.  Someone HAS to know this.  Please help.

---

### Post by Titan8990 on 2009-06-15
\ is used as an escape character. In your example, your using \ as space but that is not correct. So it needs to be:

//<server ip/name>/path/with\ 040space

The \ simply tells the shell to interpret the next character literally meaning treat it has a character space and not another directory.

---

### Post by cheddercaveman on 2009-06-16
Ok that still isn't working unfortunately.  I also rebooted my MacBook in the mean time and I'm now at least seeing that there IS a share called video (name of the share going to the filepath), but I am still not able to connect to it and I'm getting an error when I try to

I've tried having it setup the following ways..
path = /media/disk1/My\040 Documents/My\040 Videos

and

path = /media/disk1/My\ Documents/My\ Videos

Neither of them seem to be working out correctly though.  I'll probably keep trying some things, but any additional advice would be extremely appreciated

---

### Post by Celauran on 2009-06-16
Have you tried enclosing it in quotes?

```
path = "//media/disk1/with space/etc/whatever"
```

Or how about:
```
path = /media/disk1/My%20Documents/My%20Videos
```

---

### Post by cheddercaveman on 2009-06-16
Ok, so apparently it must have been a connection issue, because the thing I tried FIRST worked finally...

path = "/media/disk1/My Documents/My Videos"

Actually Celauran I just now see your response too saying the same thing (I hadn't refreshed until I hit reply again and when I scrolled down to do some copy/paste action I saw your post) so thank you as well!

---

