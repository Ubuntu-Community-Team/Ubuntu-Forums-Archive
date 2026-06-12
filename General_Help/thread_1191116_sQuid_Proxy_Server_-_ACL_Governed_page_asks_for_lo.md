---
title: "sQuid Proxy Server - ACL Governed page asks for login?"
date: 2009-06-18
forum: General Help
---

### Post by GCoffee on 2009-06-18
SOLVED - TURNS OUT SOMETHING WAS WRONG WITH THE CONFIG??


Hi,

I've just setup a squid proxy server, all is well apart from the ACL, its acting wierd.

Basically i got A rather large (17,000+ lines) blacklist thing, turned it all into one file and put it on there. I know the blacklist is setup right because i made a test one before, with only 4 lines in it. This one has exactly the same name as the old one.

Basically I have 3 main accounts:

1. My Account (No ACL Restrictions)
2. User Account (ACL Governed)
3. Test Account (ACL Governed)

However, whenever im on either the user account or the test account whenever i try to access a page under the blacklist, say a warez site, it will ask for a login instead of showing a access denied page. 

If I enter my login (No ACL Restrictions) then it will continue to the page, however if you enter no login or a user/test login it will just ask for the login again.

But i want it to show a "Access Denied" Page. I edited the ERR_ACCESS_DENIED file under /usr/share/squid/error but then, thinking this was the cause of the problem, i overwrited it with another file in that directory and edited it to say access denied.

Still didnt solve it, so now I am stuck. 

As far as I know the ACL all seem in order..

Anyone know why this is happening?

Thanks in advance,
GC.

---

