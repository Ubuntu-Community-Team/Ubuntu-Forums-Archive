---
title: "is it a bug?"
date: 2005-09-03
forum: Desktop Environments
---

### Post by clapton on 2005-09-03
When I install some applications to ubuntu I've got the problem, that I can't see the char.
I don't change the resolution and...

THis is a screenshoot normal
[IMG]http://www.alojarfotos.com/images/clapton/normal_1.png[/IMG] 


And this an example with one of the apllications that fail


[IMG]http://www.alojarfotos.com/images/clapton/def.png[/IMG] 


Can I do something to fix this?

THx :)

---

### Post by weekend warrior on 2005-09-04
Are there any configuration menu options for the application? This one doesn't look like it has standard menu bar options. Are the only apps that do this unusual or locally produced apps?  If so, it might be best to try and find the homepage of the developer and contact them directly with the problem.

---

### Post by jnk on 2005-09-04
I got the same problem with xmms...
I installed iso-8859-15 as default instead of UTF-8 to get swedish characters in LinuxDC++
But then I got that problem with XMMS, that all font shrink to unreadable.
Fixed itself when I changed back to UTF-8, but then no swe char in DC++...
But I think I can live with that. ;)

Not realy a sullotion but anyway... =)

---

### Post by clapton on 2005-09-05
Yes, I've got the same error with xmms or xine.
I think that I've got to buy glasses.  \\:D/

---

### Post by jnk on 2005-09-06
Is there any way of running the system in UTF-8 and just an application in iso-8859-15.
Can't find any option for char set in LinuxDC++/Wulfor.
Maybe a bash script would do the trick but I don't know how to make one.

---

### Post by jobezone on 2005-09-06
[QUOTE=jnk]Is there any way of running the system in UTF-8 and just an application in iso-8859-15.
Can't find any option for char set in LinuxDC++/Wulfor.
Maybe a bash script would do the trick but I don't know how to make one.[/QUOTE]
 I'm not in front of linux, but I think there is a way. In a terminal type something like
> LANG=ISO-8859-15
or
> export LANG=ISO-8859-15

then execute the application in that terminal.

I'm not sure if these are the exact commands to change the charset, though.:/

---

