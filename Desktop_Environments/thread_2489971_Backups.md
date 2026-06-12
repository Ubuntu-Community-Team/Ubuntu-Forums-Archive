---
title: "Backups?"
date: 2023-08-16
forum: Desktop Environments
---

### Post by gerb006 on 2023-08-16
I'm posting this in the general forum even though I'm using development version. This seems like a super silly question. 

Has Ubuntu always had a backup utility in the desktop environment? I've always manually made a copy of my home directory in the cloud when performing a fresh install. If this utility was always there and I could have simply made use of it, I feel real silly.


J

---

### Post by deadflowr on 2023-08-16
> Has Ubuntu always had a backup utility in the desktop environment?
Not always, but for a while at least.

i wouldn't call you silly for not using it.
It's...interesting...as a backup program.

Lots of users hate it because it's rather opaque in how it works.
And it can be temperamental and minor file corruptions can mean whole swaths of backups can be lost.
And if not totally lost, very difficult to retrieve.

But it has nifty upsides like easy to encrypt (I think its the default setting), 
and easy to setup a backup location like a cloud drive or a remote server or even a simply external drive.

Sadly they've removed the best feature it had which was the ability to directly restore from previous backups inside the Files app.
(wherein you could open Files, go to any fie that you had backed up previously right click it and select the option to restore previous version, and t would open a list of all backed up versions,
and you could just select the version you wanted to restore.)

It uses duplicity backups as it's backend.
fwiw

---

### Post by gerb006 on 2023-08-16
Thank you for your detailed explanation. I don't really like the fact that it saves to .gpg files and I'm not able to easily browse/retrieve individual files/directories. But I love the space savings. The backup is a fraction of the size of my entire zipped home directory.

---

