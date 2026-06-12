---
title: "ubuntu unable to connect to websites that start with -"
date: 2006-01-09
forum: General Help
---

### Post by dhr on 2006-01-09
Any brower in ubuntu is unable to connect to any website that start with a -

Example, -method-.deviantart.com is my deviantart page, ubuntu is unable to access it, but I can on my windows box.  

I have two notebooks running the ubuntu, and they both have this issue.

Could a few of you confirm this for me.
Please try to goto -method-.deviantart.com

Does anyone have any other websites that start with a -

---

### Post by Word on 2006-01-09
[QUOTE=dhr]Any brower in ubuntu is unable to connect to any website that start with a -

Example, -method-.deviantart.com is my deviantart page, ubuntu is unable to access it, but I can on my windows box.  

I have two notebooks running the ubuntu, and they both have this issue.

Could a few of you confirm this for me.
Please try to goto -method-.deviantart.com

Does anyone have any other websites that start with a -[/QUOTE]

i dont believe that any website can start with - please try it without.

---

### Post by casper_2095 on 2006-01-09
[http://www.faqs.org/rfcs/rfc2396.html](http://www.faqs.org/rfcs/rfc2396.html)

2.3. Unreserved Characters

   Data characters that are allowed in a URI but do not have a reserved
   purpose are called unreserved.  These include upper and lower case
   letters, decimal digits, and a limited set of punctuation marks and
   symbols.

      unreserved  = alphanum | mark

      mark        = "-" | "_" | "." | "!" | "~" | "*" | "'" | "(" | ")"

   Unreserved characters can be escaped without changing the semantics
   of the URI, but this should not be done unless the URI is being used
   in a context that does not allow the unescaped character to appear.

---

### Post by aysiu on 2006-01-09
I don't see why you should ever have a URL that starts with **-**.
[http://method.deviantart.com](http://method.deviantart.com) works just fine (see attached screenshot).

---

### Post by dhr on 2006-01-10
[QUOTE=aysiu]I don't see why you should ever have a URL that starts with **-**.
[http://method.deviantart.com](http://method.deviantart.com) works just fine (see attached screenshot).[/QUOTE]


That's fine, if my username on deviantart was method, but it's -method-

try -method-.deviantart.com on a windows computers, or any other platform, you will see that it works just fine.   I would simply change my username if I could, but that's its not possible.

---

### Post by slux on 2006-01-10
Had no problems accessing. I do it thru a proxy currently though.

---

### Post by dhr on 2006-01-10
Awesome, I too was able to use a proxy and connect to my page [http://-method-.deviantart.com](http://-method-.deviantart.com)

I don't have to format my computer now, thanks, I can live with this..


One small thing, I put in a proxy for http sites, but Firefox 1.5 doesn't want to use it, but Galeon Web Browser works with the proxy, is there any trick to get firefox to use the proxy as well

---

### Post by lamego on 2006-01-10
Just go to the Firefox, Edit -> Prefences and configure your proxy on the connection settings.

---

### Post by dhr on 2006-01-10
oh yeah, it's up and running, thanks a bunch, I can now access my page

---

