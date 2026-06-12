---
title: "linux email + thunderbird question"
date: 2009-04-11
forum: General Help
---

### Post by nocloud on 2009-04-11
when i read email from an imap server using the mail command in linux, it automatically moves the message into this thing called mbox.

when i check my mail using thunderbird, i don't see any of the messages in mbox.

so my questions are
1) is it possible for thunderbird to read the mbox message?
2) is it possible to move message from mbox back into the linux inbox?

---

### Post by cwsnyder on 2009-04-11
If you are using an IMAP server, you should still have the messages in the server inbox.

I am sorry, I don't know enough to answer your questions about reading or moving messages from mbox to Thunderbird.  I know the messages in Thunderbird do not seem to be HTML.

---

### Post by albinootje on 2009-04-11
> **nocloud said:**
> 
1) is it possible for thunderbird to read the mbox message?
2) is it possible to move message from mbox back into the linux inbox?

So.. you are using ssh to login to that imap-server.
With secure copy you can copy the mbox to your hard disk, and then you can copy it into the "Local Folders" structure of Thunderbird.
For example :
cp mbox .mozilla-thunderbird/6y3eoeb9.default/Mail/Local\ Folders/
Restart Thunderbird after this, and it be visible. I've just tested it.

---

### Post by nocloud on 2009-04-11
thanks, copying the mbox file did the trick.

---

