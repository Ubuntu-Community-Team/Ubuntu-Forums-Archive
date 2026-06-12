---
title: "Minimal Ubuntu, Firewall Question"
date: 2009-03-02
forum: General Help
---

### Post by GreenDance on 2009-03-02
Hi, I'm running a minimal install of ubuntu on my spare machine, I love it as I'm learning text based stuff, instead of the gui way which is what i'm use to, my question is I am using a netgear router, should I still install UFW on my spare machine,

Edit: I'm running apache/php & mysql :)

Thank You ):P

---

### Post by lykwydchykyn on 2009-03-02
You can, though it would be redundant.  Redundancy isn't exactly a bad thing in security, though someone would have to hack your router first to get to the point where ufw would be protecting you from anything the router wasn't.

On the downside, it's one more layer of security to deal with when you're setting something up.  So you have to decide if it's past the point of diminishing returns.

---

### Post by brian_p on 2009-03-02
> **GreenDance said:**
> 

. . . . . my question is I am using a netgear router, should I still install UFW on my spare machine,

Edit: I'm running apache/php & mysql

These are the only two services you are offering - all other tcp ports on the computer are closed. With or without a router only apache or mysql will accept connections. Installing ufw is superfluous.

---

### Post by GreenDance on 2009-03-02
> **brian_p said:**
> These are the only two services you are offering - all other tcp ports on the computer are closed. With or without a router only apache or mysql will accept connections. Installing ufw is superfluous.

Thanks, I am going to be installing a ftp server shortly, need to get my web files on there somehow :),

---

### Post by brian_p on 2009-03-02
> **GreenDance said:**
> Thanks, I am going to be installing a ftp server shortly, :)

If I'd known that I'd have written 'three' and not 'two' in my previous post.:)

---

### Post by GreenDance on 2009-03-02
> **brian_p said:**
> If I'd known that I'd have written 'three' and not 'two' in my previous post.:)

:) I only just relised I forgot about the ftp server :lolflag:

---

### Post by GreenDance on 2009-03-03
Hi, is there a simple way to setup proftpd, thank you ):P

---

### Post by lykwydchykyn on 2009-03-03
webmin has a nice proftpd interface; it's what I usually use.

---

### Post by GreenDance on 2009-03-03
> **lykwydchykyn said:**
> webmin has a nice proftpd interface; it's what I usually use.

Thank you but I don't want to install CGI.

---

### Post by lykwydchykyn on 2009-03-03
Well there's also gproftpd, which is a GTK gui.  I've not used it more than to look over it, but it seems simple enough.  Otherwise, the config file isn't that complicated.

---

