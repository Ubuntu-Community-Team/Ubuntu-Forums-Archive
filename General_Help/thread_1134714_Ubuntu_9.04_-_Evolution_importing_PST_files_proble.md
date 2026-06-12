---
title: "Ubuntu 9.04 - Evolution importing PST files problem"
date: 2009-04-23
forum: General Help
---

### Post by costamatrix on 2009-04-23
hi guys!

i am trying to import my PST file (from outlook 2003) into Evolution...

but without success...


i saw in the help screen , a picture of the "Import assistante" where there was an option "File type: Outlook personal folder (*.pst)" ....

but here do not have this option...

someone know how to import a PST? if this feature DOES exists...

---

### Post by johnzollo on 2009-04-27
BUMP!!! I have the same problem.  It has to do with a library or something I think.  There might be a bug in launchpad.  Let me look into it.

john

ANYBODY ACTUALLY KNOW????

---

### Post by johnzollo on 2009-04-27
it's libpst -- working on more answers...

---

### Post by johnzollo on 2009-04-27
Ok, here's the deal.  The libpst had to be upgraded, but it seems like it wasn't ready yet.  So, even though libpst is ready to go, evolution was provided in hardy WITHOUT the PST import capability.  So, in otherwords, we are going to have to wait for an update to come out that adds the PST import to the ubuntu install of Evolution.  Until then... we wait.

Here's the link on the bug:
[https://bugs.launchpad.net/debian/+source/libpst/+bug/317602](https://bugs.launchpad.net/debian/+source/libpst/+bug/317602)

Have patience!!!

Sincerely,
john

---

### Post by johnzollo on 2009-05-08
This bug too:

[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/349312](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/349312)

working on a work-around...

john

---

### Post by johnzollo on 2009-05-08
Ok, I built Evolution from source with the PST plugin enabled (as described by the debdiff on launchpad).  Now PST import appears in "plugins", but Evolution won't show it as an option when importing.

Does anyone have any ideas?  There doesn't seem to be any progress on this and I'd PLEASE like to get it work!!!

Thank you!

Sincerely,
john

---

### Post by johnzollo on 2009-05-08
**[size="5"]please help!!!![/size]**

---

### Post by technocp on 2009-05-09
have you tried exporting in csv format from outlook and then import it to evolution. Please try it and post your reply

---

### Post by johnzollo on 2009-05-12
I no longer have Outlook.  (I was using a pirated [warez] copy and have chosen not to use pirated software anymore.)  So no, I have not tried using outlook.  I did use the new readpst utility.  That worked pretty well.  That's a decent hack in the meantime.  I recommend using the MH file format (whatever that means)-- it seems to work better when bringing the files in evolution.  Either way -- it's currently a hack.


john

---

### Post by AnRkey on 2009-06-08
This is a big problem for me too. I installed this after telling my client that they could now import all their stuff in to Evolution. The problem is I need to import thousands of reminders, emails and contacts.

Please could anyone post a hack or workaround for this?

R

---

### Post by Fcampo on 2010-02-24
I've tried on 9.10 and run smooth... thank you very much for the directions.:popcorn:

---

