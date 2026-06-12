---
title: "how to enable the ls feature in whois command.."
date: 2009-03-15
forum: General Help
---

### Post by shredder12 on 2009-03-15
i was trying to use the zone transfer feature of whois command..
and when i tried to use ls command..
i got the foloowing error..

```
 ls is not implemented
```

what does that mean??
can i implement it some how...??

any  help will be appreciated..

---

### Post by Kevbert on 2009-03-15
If you type 
```
man whois
```
you'll find that ls doesn't exist as an option.
You can get additional info with
```
whois --help
```

---

### Post by shredder12 on 2009-03-15
so does that mean .. there is no way to use the ls feature of whois...
may be i can install whois from source code.. and get ls feature enabled...
will that work??
and could anyone tell me why won't they provide ls feature with whois anymore..??

---

### Post by shredder12 on 2009-03-15
bump.. (sorry.. there was some misunderstanding..)..

---

### Post by oldos2er on 2009-03-15
There is a bunch of whois code here: [http://www.sourcecodeonline.com/list?q=whois](http://www.sourcecodeonline.com/list?q=whois) (note not all this code is freeware).

 After reading [http://scott.yang.id.au/2008/01/command-line-whois-safer-not-quite/](http://scott.yang.id.au/2008/01/command-line-whois-safer-not-quite/) , you might want to look into [http://www.gnu.org/software/jwhois/](http://www.gnu.org/software/jwhois/) . Not sure if it has ls enabled. jwhois is in the repositories.

---

