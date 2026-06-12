---
title: "Redirecting email delivery failures"
date: 2012-06-12
forum: Desktop Environments
---

### Post by bencouve on 2012-06-12
Hello Experts!

Is it possible to redirect delivery failures using postfix sendmail. If the command was something like this ..

sendmail -f [email]sender@example.com[/email]  (-?) [email]email_failures@example.com[/email] [email]receiver@the_client.com[/email]


where the (-?) is a flag to redirect failed emails?

Thanks in advance for your input.

---

### Post by SeijiSensei on 2012-06-12
Usually non-delivery notices are sent to the "postmaster" account on the server.  Look in /etc/aliases and see where that points; typically it's an alias for "root".  Replace that entry with:

```
postmaster:  email_failures@example.com
```

then run the command "sudo newaliases".

---

### Post by bencouve on 2012-06-12
Ok. I see what you mean. However, I have set up thunderbird with POP3 for receiving and SMTP for sending...

When sending I want the recipient to receive from 
[email]Alex@thecompany.com[/email]
Alex being my business compatriot
and delivery failures, if any, going to me
[email]ben@thecomany.com[/email]
Ben being me.
So that Alex won't get p... off that he gets delivery failures. So, I was hoping to be able to flag this some how.

sendmail -f [email]alex@thecompay.com[/email] (-?) [email]ben@thecompany.com[/email] [email]joe_blogs@theclient.com[/email]

where the delivery failures are sent to me. I have read somewhere that this was possible with previous versions of postfix but not with the current version so just checking with the experts.

---

### Post by bencouve on 2012-06-12
Forget this one. I sorted it...

---

