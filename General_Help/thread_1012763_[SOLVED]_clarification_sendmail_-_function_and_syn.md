---
title: "[SOLVED] clarification: sendmail - function and syntax"
date: 2008-12-16
forum: General Help
---

### Post by lamikins on 2008-12-16
Hi,
This may be an overly remedial question, but with sendmail or sendmail.pl am I correct in assuming that you can use MTA to send mail to some recipient, arbitrary_address@arbitrary_domain, and have them see a return address that is, say, a gmail account?

To clarify - I enter at CLI something like (yes, VERY dubious syntax):

sendmail -f [email]desired_return_address@gmail.com[/email] "body of the message" arbitrary_address@arbitrary_domain

Will/can the intended recipient see the desired return address and 'reply' accordingly?  Or am I perhaps (self) deluded...

PS I would check this by sending myself something, but MTA is not playing nice at the moment.

Thanks for considering this!

---

### Post by Bachstelze on 2008-12-16
1) No space between the -f flag and the From: address.
2) The message body is read on stdin.

That means you have (at least) three ways:

```
$ echo "This is a test message." | sendmail -fme@domain.com otherdude@otherdomain.com
```

```
$ sendmail -fme@domain.com otherdude@otherdomain.com < myMessage.txt
```

```
$ sendmail -fme@domain.com otherdude@otherdomain.com
Hi!

This is a test message.

Have a nice day. :)
.
```

(In the last one, notice the single period on the last line, which tells sendmail that you're done typing your message. It will *not* be included in the message.)

---

### Post by lamikins on 2008-12-16
Wow, thank you so much this is exactly what I was looking for.  

Thread solved!

---

