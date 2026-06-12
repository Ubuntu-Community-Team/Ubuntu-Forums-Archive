---
title: "Pan Error"
date: 2009-01-29
forum: General Help
---

### Post by Old Fart on 2009-01-29
Pan has quit working. When I launch it the main window opens for just a second and then closes. When I start from the console this is the message that pops up.

harry@papa:~$ pan
pan: headers.cc:264: void pan::DataImpl::load_article(const pan::Quark&, pan::Article*, const pan::StringVie                          w&): Assertion `!node->_article' failed.
Aborted

I am running Pan 0.132 on Kubuntu Hardy

Can anyone tell me this means and also how to fix it

---

### Post by khedron on 2009-01-29
This is just an internal program error. It shouldn't have occurred in the first place - assertions are used to check for programming errors.

Remember that Pan's version number is 0.xxx, which means that it is in beta, so errors are to be expected.

See if you can downgrade Pan.

---

### Post by dcstar on 2009-01-29
> **khedron said:**
> This is just an internal program error. It shouldn't have occurred in the first place - assertions are used to check for programming errors.

Remember that Pan's version number is 0.xxx, which means that it is in beta, so errors are to be expected.

See if you can downgrade Pan.

I actually switched back from the beta Pan to the old version - you can get it from the Ubuntu packages site:

[http://packages.ubuntu.com/dapper/pan](http://packages.ubuntu.com/dapper/pan)

---

