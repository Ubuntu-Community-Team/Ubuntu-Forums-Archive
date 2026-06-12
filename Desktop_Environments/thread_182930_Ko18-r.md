---
title: "Ko18-r"
date: 2006-05-27
forum: Desktop Environments
---

### Post by jimw on 2006-05-27
I have a couple of things written in KO18-R (Cyrillic) encoding.  Unfortunately, in general Unicode encoding, they come out looking like gibberish.

Anyone know where I can get a ko18-r font for Ubuntu?

JimW

---

### Post by xyz on 2006-05-27
> I resolve the problem with cyrillic.I start Lazarus with :

$LANG=mk_MK.iso88595 lazarus 
Someone seem to have solve part of the problem here:
[http://www.lazarus.freepascal.org/index.php?name=PNphpBB2&file=viewtopic&p=10539](http://www.lazarus.freepascal.org/index.php?name=PNphpBB2&file=viewtopic&p=10539)

---

### Post by jimw on 2006-05-27
Seems to me all this is doing is altering the language of the machine to Macedonian. 

Near as I can understand, iso88595 isn't really related to ko18-r

I'll try it in the last resort, though.

JimW

---

### Post by adamkane on 2006-05-27
Please describe your situation in detail, otherwise there is no way to give you specific advice.

---

### Post by jimw on 2006-05-27
[QUOTE=adamkane]Please describe your situation in detail, otherwise there is no way to give you specific advice.[/QUOTE]

I'd thought that my initial post was fairly clear and straightforward.  A lot of the former Soviet Union still sticks with the ko18 encoding instead of going to Unicode.  Documents written in these encodings require fonts engineered for them.

I don't have such a font, and a cursory search of Google shows me no good sources.

Hence, my question: does anyone here know where I could get such fonts, and when I get them, what would be the procedure for adding them to my system?

Thanks,  

JimW

---

### Post by xyz on 2006-05-29
How about this:
[http://www-128.ibm.com/developerworks/linux/library/l-u-cyr/](http://www-128.ibm.com/developerworks/linux/library/l-u-cyr/)
This isn't easy to figure!

---

### Post by jimw on 2006-05-30
[QUOTE=xyz]How about this:
[http://www-128.ibm.com/developerworks/linux/library/l-u-cyr/](http://www-128.ibm.com/developerworks/linux/library/l-u-cyr/)
This isn't easy to figure![/QUOTE]

I went looking at this page, and some of the things on it suggested to me that koi8 ought to come with Ubuntu, or at least X11.  So I did what I should have done long time ago, and tried "Locate koi8."

Indeed, it's in there.

However, I'd already worked out what the real problem is (took me long enough).  

It's that OpenOffice can't read MDB files properly.  Checking on the drivers, I find that the only drivers that are dependable will only work for latin fonts, nothing else.

I've tried to get gmdb functioning, but I get an error message, and my query on that hasn't been answered just yet.

Thanks for your time,

JimW

---

### Post by xyz on 2006-05-31
We'll just to keep on digging...

---

