---
title: "Defalt folders clash with my IMAP folders"
date: 2009-01-26
forum: General Help
---

### Post by Nils Grimsmo on 2009-01-26
Hello!

I have the folders "Trash" and "Junk" on my IMAP account.  But when I started Evolution for the first time, it created some other folders "Trash" and "Junk" too.  All four are shown, but the latter have ``fancy icons''.  These are not shown in any way on the server, as far as I can see.  There is only one "Inbox" folder though, which is my original, even though it has a fancy icon.

How can I get Evolution to use my IMAP folders for "Junk" and "Trash"?

I had to start using Evolution because my girlfriend was asking "What are you doing now?" every other minute while I was reading my e-mail.

Here is the contents of ~/.evolution/mail/config:

et-expanded-imap:__nilsgri@feiten.idi.ntnu.no_._23evolution_Junk
et-expanded-imap:__nilsgri@feiten.idi.ntnu.no_._23evolution_Trash
...
et-expanded-imap:__nilsgri@feiten.idi.ntnu.no_INBOX
et-expanded-imap:__nilsgri@feiten.idi.ntnu.no_Junk
...
et-expanded-imap:__nilsgri@feiten.idi.ntnu.no_Trash
...
et-expanded-mbox:_home_nilsgri_.evolution_mail_local_._23evolution_Junk
et-expanded-mbox:_home_nilsgri_.evolution_mail_local_._23evolution_Trash
et-expanded-mbox:_home_nilsgri_.evolution_mail_local_Inbox
folder-tree-expand-state.xml
gtkrc-mail-fonts


Klem fra Nils

---

