---
title: "Evolution mail issue"
date: 2009-01-26
forum: General Help
---

### Post by Ketara on 2009-01-26
I was recently fiddling with Evolution to see how/if I might like it, and I didn't realize that the settings I had set up for my e-mail account (mail.ucla.edu) would set it to erase all of my emails from the actual mail server. Since I don't carry my computer with me everywhere I go, I don't want it to do that. I've since changed the settings to make sure it does not do that.

However, I am wondering if there is a way to transport the emails from the Evolution account back to the mail server. I haven't been able to find any info on doing something like this.

Thanks.

---

### Post by Saghaulor on 2009-01-27
I'm no expert on email, but you could always forward them back to yourself.

Make sure you have enabled to leave the messages on the server, or else it will download the forwarded email and promptly delete it: leaving you back at square one.

It's not a pretty way of doing it, but it will work.

---

### Post by jonobr on 2009-01-27
Sounds like your using a pop3 server to get your email?

Typically POP by default will remove all emails from the server after it has downloaded them,


You cant put them back, you could as recommended email them back to yourself, that means it changes the from field making it difficult to find what you need
You could just back them up for futher use later on.

All your emails are stored in a hidden directory in your home folder (open home folder , hit control h to show hidden folders.
In there is evolution, If you look around, you find recommendation to assist in backups.

---

### Post by quirks on 2009-01-31
Evolution has a redirect feature, which keeps the sender and recipient intact.

1. Highligh the message to be reuploaded.
2. Go to Message -> Forward as ... -> Redirect.
3. Send it to yourself.

However, I noticed that it will screw up the date, the e-mail was originally sent. Also, it only works on a single mail. You cannot apply it to multiple e-mails at once.

There seems to be a Thunderbird plug-in "mailredirect", which (supposedly - I haven't tested it myself) allows you to bounce a whole bunch of e-mails back to your account. It can be found here: [http://mailredirect.mozdev.org/installation.html](http://mailredirect.mozdev.org/installation.html)
You will have to convert your mailbox to a format understood by Thunderbird, though.

I'm feeling sorry for all the trouble you have ... :(
Those were the best solutions I could come up with.

---

### Post by dcstar on 2009-02-01
> **Ketara said:**
> I was recently fiddling with Evolution to see how/if I might like it, and I didn't realize that the settings I had set up for my e-mail account (mail.ucla.edu) would set it to erase all of my emails from the actual mail server. Since I don't carry my computer with me everywhere I go, I don't want it to do that. I've since changed the settings to make sure it does not do that.

However, I am wondering if there is a way to transport the emails from the Evolution account back to the mail server. I haven't been able to find any info on doing something like this.

Thanks.

Set up the account as IMAP, then drag and drop the messages from the existing Inbox to the new IMAP one.

---

