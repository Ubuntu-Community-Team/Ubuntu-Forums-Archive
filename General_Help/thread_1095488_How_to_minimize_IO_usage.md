---
title: "How to minimize I/O usage"
date: 2009-03-13
forum: General Help
---

### Post by sunrex on 2009-03-13
I'm going to colocate soon and I need to know how to lower/minimize I/O usage/requests.

Because I have 2GB ram I can lower the swap quite a bit but not enough.

Right now my current thoughts are this:

80GB HDD SATA 3.0Gbps - OS/Apache2/MySQL/SWAP/PHP5
120 or 160GB HDD - Any other service I want to run. Large file hosting from Apache2. Backup/storage.

I'm still reluctant to use this setup because I think SWAP + OS + other crap = bad.

Any thoughts?.

---

### Post by kerry_s on 2009-03-13
> I'm still reluctant to use this setup because I think SWAP + OS + other crap = bad.

????

> how to lower/minimize I/O usage/requests

cpu? ram? other?

---

### Post by sunrex on 2009-03-13
..sigh

I'm trying to figure out how to minimize I/O usage on the HDD/HDD's.

AKA, I'm trying to figure out if the I/O usage will be to much for one HDD with MySQL/Apache2/PHP5/SWAP/OS/SSH/other(Whatever else I install).

You're HDD can only have so many I/O requests before they are put in a queue (My understanding anyway). And once that happens things tend to slow down.

So I was trying to figure out if I should have one small HDD (80GB) for the OS/SWAP/MySQL/SSH. And have a larger one (Say 160GB) for the rest.

Thus, lowering I/O requests on one of the HDD.

But since it's a small server I'm unsure if it's needed.

---

### Post by sdennie on 2009-03-14
The only way to know for sure is to try it under the load you except the server to have.  My guess is you won't need the smaller disk because you probably won't use any swap and once the OS is started, the small fraction of it that's being regularly used will be quickly living in the cache (though, you may still have some writes to logs).  But, again, the only way to know for sure is to try it under the load you expect the server to generally have.  You are probably going to find that adding RAM is going to be cheaper and a better upgrade for performance than adding a second small disk.

---

### Post by sunrex on 2009-03-14
The smaller disk costs 36.00 on newegg.

---

### Post by kerry_s on 2009-03-14
those are very good spec's, i doubt you could peak them out, but than again you haven't said what the purpose of the server is.
also will it be gui or just command line? gui will use some resources.

splitting the setup will always help, so if you have 2 drives use them.
separate partions for:
/
/var
/usr
/tmp

---

### Post by dcstar on 2009-03-14
> **sunrex said:**
> ..sigh

I'm trying to figure out how to minimize I/O usage on the HDD/HDD's.

AKA, I'm trying to figure out if the I/O usage will be to much for one HDD with MySQL/Apache2/PHP5/SWAP/OS/SSH/other(Whatever else I install).

You're HDD can only have so many I/O requests before they are put in a queue (My understanding anyway). And once that happens things tend to slow down.

So I was trying to figure out if I should have one small HDD (80GB) for the OS/SWAP/MySQL/SSH. And have a larger one (Say 160GB) for the rest.

Thus, lowering I/O requests on one of the HDD.

But since it's a small server I'm unsure if it's needed.

Spreading the work between more disks will always spread the load, how much and how effective cannot be answered by your "how long is a piece of string?" question.

You need to know specifics on how hard your various apps are utilised and how well your environment performs, system tuning in this manner takes time and expertise that cannot be answered in anything but broad terms in a forum like this.

---

