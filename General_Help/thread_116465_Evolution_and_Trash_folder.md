---
title: "Evolution and Trash folder"
date: 2006-01-12
forum: General Help
---

### Post by Bachstudies on 2006-01-12
Dear All,

Does anyone have a problem with moving emails to different folders in evolution? Whenever I do it, as well as getting a correctly moved email I also end up with one copy in the trash folder. Is this normal? I'm just going on what I'm used to in Thunderbird and Outlook.

---

### Post by dcstar on 2006-01-12
[QUOTE=Bachstudies]Dear All,

Does anyone have a problem with moving emails to different folders in evolution? Whenever I do it, as well as getting a correctly moved email I also end up with one copy in the trash folder. Is this normal? I'm just going on what I'm used to in Thunderbird and Outlook.[/QUOTE]
Just noticed the same thing in my Evolution, look like a bug.

BTW, emptying the Trash folder does not remove the moved e-mail.

---

### Post by dcstar on 2006-01-13
[QUOTE=dcstar]Just noticed the same thing in my Evolution, look like a bug.

BTW, emptying the Trash folder does not remove the moved e-mail.[/QUOTE]
Ha!, I reported it as a bug and got the answer back that it is a "Feature".

To quote the reply:

[I]------- Comment #1 from Karsten Bräckelmann  2006-01-14 00:38 UTC -------
This is intended behaviour. Moving a mail actually is "copy and delete". This is just fine and actually the preferred way for some mail storages types.

Deleting a mail actually marks the mail for deletion. The "Trash" folder
actually is not a real folder, but a vFolder (named Search Folder since 2.4).
It just displays all mails that are marked-for-deletion. To see this for
yorself, please disable "View / Hide Selected Mesages". You will note that the
supposedly deleted mail is in your source folder -- exactly the mail you just
moved.

This is not a bug, but a feature. :)[/I]

---

