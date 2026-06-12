---
title: "Recent forums downtimes - 160713"
date: 2016-07-13
forum: Forum Feedback &amp; Help
---

### Post by bapoumba on 2016-07-13
You may have noticed :)
The forums db needed to be worked on after it went a bit berserk and was stuck on locked processes. Thanks to canonical-sysadmins, namely fo0bar, we are back and alive.

We may need additional work on the db, hopefully with scheduled downtimes.
[QUOTE=canonical-sysadmin]..but the core problem is all of the
> tables in the master DB were vbulletin default MyISAM, which was causing
> entire table locks on the user table (which almost any action updated),
> and sometimes the threads table.  As a result, runaway lock waiting
> processes were piling up.
>  
> I've converted the tables to InnoDB which allows for per-row locking,
> and things seem to be better.  Eventually we should probably convert all
> tables, but the posts table is likely to result in several hours of hard
> downtime, and this appears to be sufficient for now.[/QUOTE]
[QUOTE=me]..If you think all the db tables need to be converted, you should do it  
imho. Users will understand and accept forums downtime if they know ahead  
of time. The forums have been unusable for several days now, we did not  
have any explanation to give them, which is one of the worse situation for  
a site that has a strong social component ..[/QUOTE]
 
We'll see and keep you posted with any further info.

I'm quite sorry about the recent forums outages, please accept my apologies.

---

### Post by ventrical on 2016-07-13
> **bapoumba said:**
> You may have noticed :)
The forums db needed to be worked on after it went a bit berserk and was stuck on locked processes. Thanks to canonical-sysadmins, namely fo0bar, we are back and alive.

We may need additional work on the db, hopefully with scheduled downtimes.


 
We'll see and keep you posted with any further info.

I'm quite sorry about the recent forums outages, please accept my apologies.

Today it completely shut down with server error - but it is back again :)

regards..

---

### Post by bapoumba on 2016-07-13
> **ventrical said:**
> Today it completely shut down with server error - but it is back again :)

regards..
Yes, many thanks to fo0bar from the canonical-sysadmins who worked real hard :)

---

### Post by bapoumba on 2016-07-14
For info, all the tables have been converted, that took several hours (posts table is, well, huge). In the process, some issues with the slave server had to be dealt with.
Hopefully we are back on sane tracks, many thanks fo0bar once again :)

---

### Post by Bashing-om on 2016-07-14
: hey;

My recent observation is the forum is now running quick and smooth ..

Pats on the back to all who got us back in shape .

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]together we can
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by uNoubu8a on 2016-07-15
Up up up and down, turn turn turn around... so it was down and is now back up...

---

### Post by bapoumba on 2016-07-15
Yes hopefully all the work is done :)

---

### Post by Bashing-om on 2016-07-15
bapoumba; Hey ...

This has come to my attention 

[https://insights.ubuntu.com/2016/07/15/notice-of-security-breach-on-ubuntu-forums/](https://insights.ubuntu.com/2016/07/15/notice-of-security-breach-on-ubuntu-forums/)

Maybe make others here aware also of what has transpired ?

[INDENT][INDENT]bbad bad people
[/INDENT][/INDENT]

---

### Post by bapoumba on 2016-07-15
Yeah, thanks Bashing-om, now you know as much as we do :)

---

### Post by PaulW2U on 2016-07-15
> **Bashing-om said:**
> [https://insights.ubuntu.com/2016/07/15/notice-of-security-breach-on-ubuntu-forums](https://insights.ubuntu.com/2016/07/15/notice-of-security-breach-on-ubuntu-forums)
> **bapoumba said:**
> Yeah, thanks Bashing-om, now you know as much as we do :)
Wow, had no idea as a mere bystander trying to access the forums and monitoring IRC.

Full marks to Canonical for giving us a detailed report of what happened though.

---

### Post by &amp;KyT$0P# on 2016-07-15
> **Bashing-om said:**
> This has come to my attention 

[https://insights.ubuntu.com/2016/07/15/notice-of-security-breach-on-ubuntu-forums/](https://insights.ubuntu.com/2016/07/15/notice-of-security-breach-on-ubuntu-forums/)
Thank you for being transparent about that.  Is it known whose user data was breached / not breached?

---

### Post by bapoumba on 2016-07-15
Yes Paul :)

---

### Post by bapoumba on 2016-07-15
> **halogen2 said:**
> Thank you for being transparent about that.  Is it known whose user data was breached / not breached?
All we know is in the report.

---

### Post by mörgæs on 2016-07-15
> **PaulW2U said:**
> 
Full marks to Canonical for giving us a detailed report of what happened though.

+1

I wonder why people are interested in downloading such a table. For selling the e-mail addresses to a spammer?

---

### Post by bapoumba on 2016-07-15
> **mörgæs said:**
> +1

I wonder why people are interested in downloading such a table. For selling the e-mail addresses to a spammer?
Yeah, and bragging about, this is so foreign to me. And may be just do it because it can be done if you are interested into destroying ?

---

### Post by The Cog on 2016-07-17
Could it be that the excessive table locking on the user table was caused by all the table reading by the break-in? 
Just wondering from an entirely database perspective.

---

### Post by bapoumba on 2016-07-17
> **The Cog said:**
> Could it be that the excessive table locking on the user table was caused by all the table reading by the break-in? 
Just wondering from an entirely database perspective.
I have no experience/knowledge with/about db. We had two set of downtimes happening. First ones when IS was working on changing the db engine, then when the hack was made public by the hacker itself and confirmed by IS. There was a time gap between these two events (and the forums were flying fast after IS worked on the db), not sure they are related, but I do not know and have no way of knowing.

---

