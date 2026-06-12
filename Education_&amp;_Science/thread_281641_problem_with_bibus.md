---
title: "problem with bibus"
date: 2006-10-21
forum: Education &amp; Science
---

### Post by machoo02 on 2006-10-21
Hi,

I've been having a little trouble with getting bibus working.  Goes through the normal install fine, sets up the OO.o connection, and creates a .pysqlite3 database.  However, when I try to import references via File>Import>Refer (Endnote), bibus just hangs.  Had this same problem when I tried to install bibus in Windows.  Any thoughts/solutions?  Would love to save my bibliography from the 3rd circle demon known as Thompson ResearchSoft.

**Edit**:
Ok, so I found the solution on the Bibus Wiki page @ SourceForge.  The important part is formatting your references in the 'Endnote Export' format before exporting.  Funny, I read that page probably 5 times in frustration, and that one line seems to have escaped my attention every time.

---

### Post by akniss on 2006-10-24
> **machoo02 said:**
> Hi,

I've been having a little trouble with getting bibus working.  Goes through the normal install fine, sets up the OO.o connection, and creates a .pysqlite3 database.  However, when I try to import references via File>Import>Refer (Endnote), bibus just hangs.  Had this same problem when I tried to install bibus in Windows.  Any thoughts/solutions?  Would love to save my bibliography from the 3rd circle demon known as Thompson ResearchSoft.

**Edit**:
Ok, so I found the solution on the Bibus Wiki page @ SourceForge.  The important part is formatting your references in the 'Endnote Export' format before exporting.  Funny, I read that page probably 5 times in frustration, and that one line seems to have escaped my attention every time.

So does this mean you have a working Bibus installation on Edgy?  This is one of the things keeping me on Dapper.  I'm scared that if I upgrade it will take me days to get Bibus working properly again...

---

### Post by machoo02 on 2006-10-26
> **akniss said:**
> So does this mean you have a working Bibus installation on Edgy?  This is one of the things keeping me on Dapper.  I'm scared that if I upgrade it will take me days to get Bibus working properly again...

So far, so good.  I've had no problems with Bibus so far (although I am relatively new to using it, so it could be that I just haven't pushed it far enough to break).

---

### Post by euphro on 2006-11-02
Thanks for the info on this.  I spent a frustrating few hours on Saturday trying to import my Endnote library into bibus and only succeeded in corrupting it.  I've had a look through the Sourceforge bibus wiki but I haven't so far found the reference to using Endnote export format. Nevertheless, the pointers you've provided here have helped me solve my problem.  Thanks again :)

---

### Post by GrumpyBob on 2006-11-04
> **akniss said:**
> So does this mean you have a working Bibus installation on Edgy?  This is one of the things keeping me on Dapper.  I'm scared that if I upgrade it will take me days to get Bibus working properly again...

I had bibus working on my laptop using Breezy, updated it to Dapper and it still worked.  Upgraded to Edgy, and after failing to sort out the ensuing xserver issues did a clean reinstall.  Reinstalled Bibus and it was working just as before!  Presumably it just picked up whatever configuration files remained in my home folder (I have /home on a separate partition, so it was unaffected by the clean reinstall.

So, yes, bibus is fine with edgy.

Robert

---

### Post by akniss on 2006-11-04
> **GrumpyBob said:**
> I had bibus working on my laptop using Breezy, updated it to Dapper and it still worked.  Upgraded to Edgy, and after failing to sort out the ensuing xserver issues did a clean reinstall.  Reinstalled Bibus and it was working just as before!  Presumably it just picked up whatever configuration files remained in my home folder (I have /home on a separate partition, so it was unaffected by the clean reinstall.

So, yes, bibus is fine with edgy.

Robert

Thanks for the update, that's great news!  I will probably give edgy a go in the next week or so.

---

### Post by David Valentine on 2006-11-06
One thing to be aware of is the fact that Bibus will not check to ensure that python-pysqlite2 is installed, so if your database is in sqlite3 format, you'll just get an error when you try to open it.  It seems like python-pysqlite2 ought to be a dependency...

---

