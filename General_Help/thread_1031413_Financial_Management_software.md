---
title: "Financial Management software"
date: 2009-01-05
forum: General Help
---

### Post by Jordanwb on 2009-01-05
My question's pretty simple - hopefully: Anyone know of good financial management software for Linux?

---

### Post by 2hot6ft2 on 2009-01-05
Well there's GnuCash and KMyMoney. How good they are I couldn't say.

---

### Post by Ahadiel on 2009-01-05
> **Jordanwb said:**
> My question's pretty simple - hopefully: Anyone know of good financial management software for Linux?
gnucash, it's in the repos.
```
sudo apt-get install gnucash
```

---

### Post by Jordanwb on 2009-01-05
I'll give gnucash a try.

---

### Post by HermanAB on 2009-01-05
SQL-Ledger: [http://sql-ledger.org](http://sql-ledger.org)

Also see these:
[http://aeronetworks.ca/GNU_Cash_for_Business_users_Howto_Guide.html](http://aeronetworks.ca/GNU_Cash_for_Business_users_Howto_Guide.html)
[http://aeronetworks.ca/GnuCash.tgz](http://aeronetworks.ca/GnuCash.tgz)

and
[http://aeronetworks.ca/sql-ledger.html](http://aeronetworks.ca/sql-ledger.html)

---

### Post by oldos2er on 2009-01-05
[http://linuxappfinder.com/businessandfinance](http://linuxappfinder.com/businessandfinance)

---

### Post by JamesLavin on 2009-01-05
> **HermanAB said:**
> SQL-Ledger: [http://sql-ledger.org](http://sql-ledger.org)


I've used sql-ledger for four (?) years in my small (tiny) business and have found it quite useful, though it lacks bells and whistles.

But many FOSSers are upset with Sql-Ledger's license change and developer, so you might want to instead consider forks of SQL-Ledger (explanation for forks: [http://lwn.net/Articles/227151/](http://lwn.net/Articles/227151/) & [http://yro.slashdot.org/article.pl?sid=07/04/15/1759254](http://yro.slashdot.org/article.pl?sid=07/04/15/1759254) & [http://forums.whirlpool.net.au/forum-replies-archive.cfm/793413.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/793413.html)). The most well known appears to be LedgerSMB ([http://www.ledgersmb.org/](http://www.ledgersmb.org/)).

Also, you can apparently skip installation headaches with [http://www.vmware.com/appliances/directory/62692](http://www.vmware.com/appliances/directory/62692) or [http://wiki.ledger123.com/index.php?n=User.Virtual](http://wiki.ledger123.com/index.php?n=User.Virtual).

--James Lavin

---

### Post by lykwydchykyn on 2009-01-05
I tried several to organize finances for my side jobs, finally settled on gnucash because it seems the best fit for small-business stuff.  Unfortunately I stopped getting extra work, so I didn't get to use it much.

---

### Post by beamendslrs on 2009-01-05
I've been using LedgerSMB, a fork of SQLedger mentioned above. LSMB is properly Open Source and under development. A lot of bugs have been fixed over the last 12 months. It's rather more accountant oriented than "ordinary" user oriented, but very quick help is to hand. Out of Quasar, SQLedger, GNUCash and various Windows apps it's the best on offer I think. 

Cheers
Richard

---

