---
title: "on folder permissions"
date: 2009-06-03
forum: General Help
---

### Post by webmiester on 2009-06-03
Hi guys,

I would like to ask about folder permissions...

Firstly, I made a flashdisk and placed a restriction on onr of the folders that only my account (Let's name it username:John) can open it...

Now here's are my questions:

1) Will I be able to open the folder on a different computer running on an account with the same name (username:John?

2) If my linux suddenly gets corrupted and I need to format and reinstall it or if I upgrade it by installing a new version and I set up the same account (username:John), will I be able to access my folder on this same computer with a new OS?

Thanks so much!

---

### Post by colau on 2009-06-03
> **webmiester said:**
> Hi guys,

I would like to ask about folder permissions...

Firstly, I made a flashdisk and placed a restriction on onr of the folders that only my account (Let's name it username:John) can open it...

Now here's are my questions:

1) Will I be able to open the folder on a different computer running on an account with the same name (username:John?

2) If my linux suddenly gets corrupted and I need to format and reinstall it or if I upgrade it by installing a new version and I set up the same account (username:John), will I be able to access my folder on this same computer with a new OS?

Thanks so much!
Probably Yes, you can.

---

### Post by dcstar on 2009-06-03
> **webmiester said:**
> 
.........
Firstly, I made a flashdisk and placed a restriction on onr of the folders that only my account (Let's name it username:John) can open it...

Now here's are my questions:

1) Will I be able to open the folder on a different computer running on an account with the same name (username:John?
........

Permissions are actually numbers created by each system - your first Ubuntu user (probably) has a UID of 1001 which displays as the user name.

AFAIK plugging in the same disk into another system will display the name on that system that has the same UID - and you will have the permissions that particular user has.

---

### Post by webmiester on 2009-06-04
> **dcstar said:**
> Permissions are actually numbers created by each system - your first Ubuntu user (probably) has a UID of 1001 which displays as the user name.

AFAIK plugging in the same disk into another system will display the name on that system that has the same UID - and you will have the permissions that particular user has.

So let me clarify this: If my file on the flashdisk can only be accessed by root on my computer due to permission, I can also plug it into another computer and it's root user will also be able to access it?

Also,. if you say that it depends on the UID, then that would mean that if I setup a username:John on "computer B" but it becomes the fifth account on computer B while it is the first account on my computer (computer A), I also wont be able to open my files on computer B right?  Ill need to use computer B's first account no matter what it's name is to open it as well.  Is there a way to find out what the UID of my account is?

Also where's the security there?  Although the good news to this is that in case my computer crashes, I would still be able to access it through another computer.  Is there anyway to put a password on the folder without having to encrypt the files (because so far the encryption I found is realtime, so it will really slow down big files)?

---

### Post by mcduck on 2009-06-04
> **webmiester said:**
> So let me clarify this: If my file on the flashdisk can only be accessed by root on my computer due to permission, I can also plug it into another computer and it's root file will also be able to access it?

So where's the security there?  Although the good news to this is that in case my computer crashes, I would still be able to access it through another computer.  Is there anyway to put a password system on the folder without having to encrypt the files (because so far the encryption I found is realtime, so it will really slow down big files)?

With physical access to computer hardware there's never any security, unless you encrypt your data.

---

