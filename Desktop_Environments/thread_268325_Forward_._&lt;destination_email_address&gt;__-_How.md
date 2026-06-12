---
title: "Forward *.* &lt;destination email address&gt;  - How and which program?"
date: 2006-09-30
forum: Desktop Environments
---

### Post by roguenoir on 2006-09-30
So I select all the messages in this folder in Evolution, hit the forward button but it only lets me foward one message at a time. I have 900+ messages I need to move to another email accout (webmail btw.)  Is there any way I can (possibly using a different email program) to perform this "action":  ?

cp * <destination>

except the * refers to all the messages in this particular folder in Evolution, and <destination> is another email address.

---

### Post by dcstar on 2006-09-30
> **roguenoir said:**
> So I select all the messages in this folder in Evolution, hit the forward button but it only lets me foward one message at a time. I have 900+ messages I need to move to another email accout (webmail btw.)  Is there any way I can (possibly using a different email program) to perform this "action":  ?

cp * <destination>

except the * refers to all the messages in this particular folder in Evolution, and <destination> is another email address.

If the e-mail system you want to forward them to has IMAP access, set up an account in Evolution using that and then use the GUI to "drag and drop" them to that server.

The other way may be to create a filter rule that auto-forwards all messages in an Evolution folder to your new e-mail address, and then copy your existing e-mails into that folder and let the process begin.

---

### Post by aysiu on 2006-09-30
I agree with dcstar--IMAP is the way to go.

In POP3, you download messages off the server, but you can't *put* messages on the server (at least as far as I know).

In IMAP, whatever you do on the mail server is reflected in Evolution (or whatever email client you're using), and whatever you do in Evolution is also reflected on the mail server.

---

