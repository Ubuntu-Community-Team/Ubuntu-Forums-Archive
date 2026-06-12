---
title: "Weired entry in hosts-file"
date: 2007-09-12
forum: Dell  Ubuntu Support
---

### Post by necaro on 2007-09-12
Hello Guys!

I purchased a Dell Inspiron 6400n with Ubuntu preinstalled.
After having a look at my hosts file i recognized a weired entry.

in the second line it says:

```
127.0.1.1 dell.linuxdev.us.dell.com neon
```

I wonder why there is a URL from DELL!?!?

"neon" is my hostname so its ok, but what does the DELL adress their mean? 

I hope for an awnser ;)

thx so long,
necaro

---

### Post by dcstar on 2007-09-12
> **necaro said:**
> Hello Guys!

I purchased a Dell Inspiron 6400n with Ubuntu preinstalled.
After having a look at my hosts file i recognized a weired entry.

in the second line it says:

```
127.0.1.1 dell.linuxdev.us.dell.com neon
```

I wonder why there is a URL from DELL!?!?

"neon" is my hostname so its ok, but what does the DELL adress their mean? 

I hope for an awnser ;)

thx so long,
necaro
Most likely just something Dell have to put in for their default installs to work, you may want to delete it and see if anything happens...... (my "normal" Ubuntu install just has my system host stuff there).

---

### Post by necaro on 2007-09-12
Ok, i have deleted that entry now and it seems that it has no effect.

Before my hosts file looked like this:

```
127.0.0.1 localhost neon
127.0.1.1 dell.linuxdev.us.dell.com neon 
```

Afterwards it looks like this:

```
127.0.0.1 localhost neon
127.0.1.1 neon
```

But no effect at all.

But perhaps anybody knows why it is exactly there, cause I am really interested in it ;)

Best regards,
necaro

---

### Post by Linicks on 2007-09-12
FYI my Dell laptop I received last week had a similar entry in /etc/hosts file too.  I just removed it.

Nick

---

### Post by necaro on 2007-09-12
hey

I removed the entry now as well and everything seems to be normal.

But I really would like to know what it is for :D

---

### Post by gbrainin on 2007-09-12
As far as I can tell, the entire 127.X.X.X subnet is reserved for the "loopback" function.  Normally, only 127.0.0.1 is used but an entry for anything that begins with 127 will never be sent outside your computer.

My theory is that the dell.com address is something used during the setup/testing phase, and they just neglect to delete it (since it has no effect).

---

### Post by pheonixind on 2007-09-12
It is a configuration for when they are setting them up and testing them from the factory.  They test every system before they ship to make sure it works.  That .com address is most likely the internal network name for them to verify packages and the such.

---

### Post by necaro on 2007-09-12
ah ok, I go it ;

Thanks for all you awnsers:grin:

---

### Post by Linicks on 2007-09-12
There is some debate about the hosts file.

On my Slackware box, hosts file is appended with a comment from Arnt Gulbrandsen - you can read this here:

[http://ka1fsb.home.att.net/hosts.html](http://ka1fsb.home.att.net/hosts.html)

So I never append machine name to 127.0.0.1 - this should be just left for local loop.

If you have static IP assigned, then add another line WITH machine name/domain:

123.456.789.123 some.domain.net machinename

etc.

If you use DHCP, that mechanism _should_ set the (local) DNS correctly anyway in routing table (i.e. the machine knows).

But as I said, sometimes this doesn't work right - sendmail for one shouts about it.

Nick

---

### Post by necaro on 2007-09-12
so if I understood you right, you mean i can delete the 2nd line:

```
127.0.0.1 neon
```

completely??

Or have I understood something wrong?

Sorry, I am still learning english ;)

---

### Post by Linicks on 2007-09-12
No, all you should have on the first line is:

127.0.0.1 localhost

Then if you wish use the next line as you already set up:

127.0.1.1 [domain] neon

Nick

---

### Post by necaro on 2007-09-13
ah ok, thanks a lot for the information.

so long,
necaro

---

