---
title: "Evolution, IMAP, and Message Filters, oh my!"
date: 2009-02-27
forum: General Help
---

### Post by jadoti on 2009-02-27
I have an IMAP email account that I check from several computers, including my Ubuntu 8.10 install in Evolution and my iPhone.

On all systems, including iPhone, the account is setup as IMAP.

Everything works when I do things manually.  If I move a message from Inbox to FolderA in Evolution, it moves, and when I check my mail on my iPhone, I see the message in FolderA, not the Inbox.

However, when I set a message filter to move certain messages from the Inbox to FolderA upon receipt, while Evolution moves the message to FolderA as soon as it downloads, there never seems to be an "update" back to the IMAP server that the message has moved from the Inbox.  There *DOES* seem to be an update back to the IMAP server that the message is in FolderA, though.

The result, currently, is that even though Evolution is left on and checking messages, moving certain incoming emails to FolderA, on the iPhone, I have the messages in FolderA *AND* the Inbox.  Even when I do an update, or wait on the iPhone, they still appear in both FolderA and the Inbox.

I'm not sure if this is an iPhone problem or an Evolution problem, or the IMAP server inbetween, like I said, manually moving messages from Inbox to FolderA results in it showing up that way across all devices that access that email account, it's just when the message is moved by a message filter in Evolution, it doesn't seem to be updated to the IMAP server.

Any advice on how to fix, or further troubleshoot this, is greatly appreciated.

Mike

---

### Post by dcstar on 2009-02-28
> **jadoti said:**
> I have an IMAP email account that I check from several computers, including my Ubuntu 8.10 install in Evolution and my iPhone.

On all systems, including iPhone, the account is setup as IMAP.

Everything works when I do things manually.  If I move a message from Inbox to FolderA in Evolution, it moves, and when I check my mail on my iPhone, I see the message in FolderA, not the Inbox.

However, when I set a message filter to move certain messages from the Inbox to FolderA upon receipt, while Evolution moves the message to FolderA as soon as it downloads, there never seems to be an "update" back to the IMAP server that the message has moved from the Inbox.  There *DOES* seem to be an update back to the IMAP server that the message is in FolderA, though.

The result, currently, is that even though Evolution is left on and checking messages, moving certain incoming emails to FolderA, on the iPhone, I have the messages in FolderA *AND* the Inbox.  Even when I do an update, or wait on the iPhone, they still appear in both FolderA and the Inbox.

I'm not sure if this is an iPhone problem or an Evolution problem, or the IMAP server inbetween, like I said, manually moving messages from Inbox to FolderA results in it showing up that way across all devices that access that email account, it's just when the message is moved by a message filter in Evolution, it doesn't seem to be updated to the IMAP server.

Any advice on how to fix, or further troubleshoot this, is greatly appreciated.

Mike

Why not add an extra command in your filter to remove it from the Inbox?, anyway it is probably something **you** should report as a bug.

---

### Post by jadoti on 2009-02-28
> **dcstar said:**
> Why not add an extra command in your filter to remove it from the Inbox?, anyway it is probably something **you** should report as a bug.

I certainly agree about reporting it as a bug, however, I would like to ensure that it's not a user error before I cry wolf ;)

The rule to remove the email from the Inbox in Evolution would be pointless, as I stated, in Evolution, the email does properly get moved from the Inbox to FolderA per the original message filter.  i.e., there's nothing in the Inbox to delete in Evolution.

Thanks for the help anyways, 
Mike

---

