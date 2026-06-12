---
title: "viewing evolution attachments"
date: 2006-01-07
forum: Desktop Environments
---

### Post by Paranoid Randroid on 2006-01-07
Hello.

I'm a somewhat new Linux user, and a very new Evolution user.  I'm having trouble viewing attachments in Evolution - Evolution seems to automatically display, inline, the attachment in whatever encoding it was sent via.  This usually results in a bunch of garbled, meaningless ascii, unless the attachment happened to be plain text.

There doesn't seem to be any option to save the attachment, and I've looked everywhere for some way to change this default behavior, to no avail.  Help would be appreciated.

---

### Post by dcstar on 2006-01-07
[QUOTE=Paranoid Randroid]Hello.

I'm a somewhat new Linux user, and a very new Evolution user.  I'm having trouble viewing attachments in Evolution - Evolution seems to automatically display, inline, the attachment in whatever encoding it was sent via.  This usually results in a bunch of garbled, meaningless ascii, unless the attachment happened to be plain text.

There doesn't seem to be any option to save the attachment, and I've looked everywhere for some way to change this default behaviour, to no avail.  Help would be appreciated.[/QUOTE]
I don't have this issue, and I can't find anything in the Evolution preferences to alter it.

What does View-Character Encoding say?

---

### Post by Paranoid Randroid on 2006-01-07
[QUOTE=dcstar]What does View-Character Encoding say?[/QUOTE]

It says "Default", which is UTF-8.

Evolution knows it's an attachment: it clearly separates the ascii garble from the email message with a horizontal line, and there's a paperclick next to the message title in the list.  But there seems to be no way to extricate the attachment from the message.

(I suppose I should note that I'm using Evo 2.4.1, and an almost brand new Breezy install.)

---

### Post by dcstar on 2006-01-07
[QUOTE=Paranoid Randroid]It says "Default", which is UTF-8.

Evolution knows it's an attachment: it clearly separates the ascii garble from the email message with a horizontal line, and there's a paperclick next to the message title in the list.  But there seems to be no way to extricate the attachment from the message.

(I suppose I should note that I'm using Evo 2.4.1, and an almost brand new Breezy install.)[/QUOTE]
Mine doesn't behave that way, all attachments are clearly listed as such - with options to View or Save - and are not visible in the message body.

Something sounds very screwy with your setup......      :???:

You might want to save your Inbox files and do a total removal (including config files) and re-install of Evolution.

---

### Post by Paranoid Randroid on 2006-01-07
[QUOTE=dcstar]
You might want to save your Inbox files and do a total removal (including config files) and re-install of Evolution.[/QUOTE]

Hrm.  That didn't do the trick, either, which kind of scares me.  It's probably that I'm choosing some option that results in this behavior - it's very strange and cannot possibly be the default - but I have no idea what it is.  I guess I'll give Sylpheed a look, something.

Thanks, though!

---

### Post by valmiki on 2006-08-16
Hello,

I was having the same problem with Evolution 2.6.1 in Dapper.  Turned out that the server type should have been IMAPrev1 instead of IMAP.  You may want to check that you have defined the server type correctly.

Valmiki

---

### Post by kryptonik on 2007-08-24
I use Evolution as an Exchange client, not as an IMAP client, and really, really don't want to view the attachments inline.  How do I do this?

---

