---
title: "[evolution] filters not auto running"
date: 2005-12-06
forum: Desktop Environments
---

### Post by xlancealotx on 2005-12-06
Hey all, recently made the move from FC4 to Ubuntu and pleasntly surprised.  Excellent distro, so with all that behind, here is the question.  I have a few mailing list filters running (if mailing list 'x' move to folder) simple things like that, but when new mail comes in, they just sit there.  If I <ctrl> - <a> select all, then select Message, Apply filters they do as they should and move, but new mail and initial start of the app they just sit there.

Details R:
.evo version: 2.4.1
.all m'boxes are IMAP protocol
.under the mail account / recieving options / options
I do have the Apply Filters checkbox selected, check for junk selected and Only check for junk in INBOX selected.

It's not a horrible thing to have to select all and move em, but thought I would ask if NEone has seen / fixed .

tnx ..

---

### Post by nicolas314 on 2006-12-08
Same thing here running evolution 2.6.1 under Dapper. Define as many filters as you want, check out the option to apply them automatically under mail preferences, and watch your e-mail sit in your inbox.

But as you mention, you can also automatically select all e-mails with CTRL-A and choose "Filter mails" in the menu ;-)

---

### Post by bbarrons on 2006-12-17
I have 3 message filters running and they work fine. I seperate ebay messages, and 2 forums that I read. I did this in dapper and now in edgy..... they are automatic.

---

### Post by nicolas314 on 2006-12-24
Following up on my previous post: I have left all filters defined in Evolution and completely forgot about them until a couple of days later (and X restarts of said e-mail application), when the very same filters appeared to be working. I guess we could document that as a working feature, just a little slow to trigger ;-)

---

### Post by moeFinley on 2007-12-14
I have the same issue in Gutsy.  I've only just started using Evolution with my IMAP accounts after switching from Opera.  I guess I'll wait a while and see if it magically fixes itself. :(

---

### Post by bjopet on 2008-01-09
Hi,

I've read somewhere that evolution only filters mail if they don't have the flag "SEEN" set,  and this is set by the server, and a mail will be considered "SEEN" if any program interacts with the mail, for example a mail-notification agent.

My evolution is reading IMAP from an Exchange-server, and my filters worked only if i ran them manually, but after I disabled the "New Mail Notification" plugin (Edit->Plugins->uncheck NewMailNotification) the filters worked automatically.

Problem Solved, for me :-)

/Bjorn

---

### Post by adieb on 2008-03-21
oh, that would explain, why those filters work on pop while they are not working (automatically) on imap accounts! great.

just one question: where can i disable the email-notification-client?

thanks


[EDIT]
i found this by myself. but who reads this and also doesnt know: system->settings->sessions.... just disable it there
[/EDIT]

---

### Post by thegreedyturtle on 2008-07-22
I'm wondering if there's any way to set evolution to filter the new unseen messages, because I'd really like to use a mail notifier.

---

