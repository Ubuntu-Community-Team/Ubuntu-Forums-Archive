---
title: "IE inside Ubuntu"
date: 2009-08-31
forum: Desktop Environments
---

### Post by gohkimhock on 2009-08-31
hi guys, today is my 1st day usig Ubuntu.
how do i install IE inside Ubuntu. Some of my favourite websites need IE to view it.

---

### Post by cybergalvez on 2009-08-31
there used to be a project called IE for linux ([http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)) but it does not support IE past version 6 and the last time I tried it it really didn't work.  Aside from that that if you really want IE (MS does not make a native linux version) you could install virtualbox and XP.

---

### Post by binbash on 2009-08-31
You can use firefox extensions to change agent switcher to view that pages in IE. Other than installing virtual box with windows is the best way to go.

---

### Post by jacksaff on 2009-08-31
You can install ie using wine but...

Most websites that say they need ie don't - they just check the user agent string. This is done usually because the web developer was a moron, and sometimes because the company is windows (and ie) only and just didn't know any better. You should be able to access these sites by user-agent switching in any decent browser so you don't need ie.

Some sites really do need ie because they use activeX. This was a huge source of security problems in win 98 and XP days. If your site needs this then ie under wine won't help you anyway as wine doesn't support it. In this case you're stuffed (though you do have a system without ie and the awful security hole that is activeX :)).

As a result there really isn't actually much of a use case for ie under linux which is why noone has ever really bothered to get it working easily.

---

### Post by ugm6hr on 2009-08-31
> **gohkimhock said:**
> Some of my favourite websites need IE to view it.

Not wanting to be unhelpful, but you need some new favourite sites then!

Seriously, I would email the webmaster and ask them why the 2nd most popular web-broswer doesn't work on their site..

---

### Post by steveneddy on 2009-08-31
> **ugm6hr said:**
> Not wanting to be unhelpful, but you need some new favourite sites then!

Seriously, I would email the webmaster and ask them why the 2nd most popular web-broswer doesn't work on their site..

Agreed.

Maybe you aren't trying hard enough.

Try a user agent switcher for Firefox:

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

or do what all the cool kids are doing, install VirtualBox and Windows in VB, then use the seamless mode to run IE in hat looks like Ubuntu. Very cool.

---

### Post by mexlinux on 2009-08-31
I know many sites, not my favorites, but the ones I needo to interact with some suppliers that really need IE, the user agent switcher does not do the trick, I have to use ies4linux anyway....

---

### Post by anujpathania on 2009-08-31
Sites that still require IE either must Microsoft Slaves or really really archaic.

---

### Post by steveneddy on 2009-09-01
I still VirtualBox is a very good answer.

---

### Post by theZoid on 2009-09-01
> **steveneddy said:**
> Agreed.

Maybe you aren't trying hard enough.

Try a user agent switcher for Firefox:

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

or do what all the cool kids are doing, install VirtualBox and Windows in VB, then use the seamless mode to run IE in hat looks like Ubuntu. Very cool.

The cool old men are doing that too....:D

---

