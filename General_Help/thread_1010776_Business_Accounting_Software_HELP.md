---
title: "Business Accounting Software HELP"
date: 2008-12-14
forum: General Help
---

### Post by neomaximus2k on 2008-12-14
Hey guys, looking to move to Ubunto server in the next few days but struggling to find some accountancy software for my small business.

I'm moving to Ubunto for a number of reasons, mainly cost! I love open source and have participated in a number of open source products in the past (php based sadly) and I would love to develop a server that will handle most small buisiness needs!

I am a website developer so I tend to invoice both for products and services with two types of invoices, 1 is per hour 1 is per product.

I would develop an online alternative but its december and tax returns are looking around the corner, sadly I have far to much work on to start the production but hey who knows I might get round to producing one in the new year.

Anyways like i said I'm after business accounting software, must be UK and hopefully help me sort out my tax return.  Oh and either be free / opensource i've been burned bad by sage and I think its just best to go down the road of open source.

Thanks for any help and advice given

---

### Post by hikaricore on 2008-12-14
Have you tried GnuCash?  Some info here: [http://www.gnucash.org](http://www.gnucash.org)

Also you can install it from the Ubuntu repos:

> sudo apt-get install gnucash

Test it out and see if it will work for your needs.

---

### Post by neomaximus2k on 2008-12-14
Well i've jumped on my acer aspire one, sadly it isn't ubuntu but it is linpus so downloading gnucash and several others as well to see what they are like


GNU Cash would appear to be the best choice, GrisBi, Home Bank and KMyMoney are all geared towards home users, but i did like the KMyMoney GUI nice and friendly

Tiny ERP wouldn't connect to the local database which was a shame as I have quite a few clients who would be interested in that.  Oh well thanks for the help if anyone can recommend any more let me know!

---

### Post by mdebusk on 2008-12-14
> **neomaximus2k said:**
> Hey guys, looking to move to Ubunto server in the next few days but struggling to find some accountancy software for my small business.

I'll give a +1 for GnuCash. I use it for my personal books. The user mailing list is extremely helpful, by the way.

Today, the developers released version 2.2.8, if you're interested in compiling from source.

---

### Post by HermanAB on 2008-12-14
SQL-Ledger:
[http://www.sql-ledger.com/](http://www.sql-ledger.com/)

It it good for a medium sized business with hundreds of employees, multiple sites and multiple currencies.

Cheers,

Herman

---

### Post by neomaximus2k on 2008-12-17
thanks guys i'll look into sql-ledger as if its mysql then I can re-develop the frontend :)

---

### Post by MiniMe on 2009-01-26
I recommend taking a look at Frontaccounting ([http://frontaccounting.net](http://frontaccounting.net))

It's php/mysql and quite easy to use.

---

### Post by bayside04 on 2009-01-29
hi, i have tried to install the suggest GNUCASH on UBUNTU 8.  does not install without some plugin called quil-slib.

surprisingly installs on WindowsXP without anyproblems at all.

any suggestions out there......

re suggestions received have u installed the software as yet.


tnanks

---

### Post by neomaximus2k on 2009-01-29
the xp version will work as the dependencies are packaged with it but i find it crashes all the time on both my windows systems.
As for the missing quil-slib try

```

sudo apt-get install slib

```

or try
```

sudo apt-get -f install gnucash

```

you should probably do an update and upgrade as well
```

sudo apt-get update
sudo apt-get upgrade

```

---

### Post by Neural oD on 2009-01-29
another one to look at could be turbocash - just google it. As far as I'm concerned openerp looks great - but i haven't used it yet; but alas it didn't work for you.

---

### Post by Neural oD on 2009-01-29
- sorry - no that i'm thinking - look at quasar accounting, also postbooks. these might suit your needs. Also look up accounting packages in wikipedia - they are usually quite good at that

---

### Post by flameproof on 2009-01-29
> **Neural oD said:**
> - sorry - no that i'm thinking - look at quasar accounting, also postbooks. these might suit your needs. Also look up accounting packages in wikipedia - they are usually quite good at that

That would be the link then:

[http://en.wikipedia.org/wiki/Comparison_of_accounting_software](http://en.wikipedia.org/wiki/Comparison_of_accounting_software)

---

### Post by AgentZ86 on 2009-06-03
Hi all

I've been using kmymoney even for my business which seems to work well.

Having trouble finding out which ones will allow cvs data imports.

Many of the suggested accounting sites do not seem to want to tell you all from their sites if you can import data from cvs ?

Does anyone know if gnucash,turbo,postbooks etc. can the import data from cvs ?
kmymoney does not seem to do it 

Please advise thanks

---

### Post by mdebusk on 2009-06-03
> **AgentZ86 said:**
> Does anyone know if gnucash, turbo, postbooks etc. can the import data from cvs ?

Gnucash can import data from QIF, and you can very easily [convert CSV to QIF with awk]("http://wiki.gnucash.org/wiki/FAQ#Q:_How_do_I_convert_from_CSV.2C_TSV.2C_XLS_.28Excel.29.2C_or_SXC_.28OpenOffice.org_Calc.29_to_a_QIF.3F"). I do it with my 403(b) data every quarter.

---

### Post by askdpfoc on 2010-12-17
Hell everyone,
 Now a days  business are becoming very complex.So there is a need of fast business calculating software.Software provides the facility to improve the business in rapid growth rate. There are many of accounting sites available who provides accounting related solutions.

---

