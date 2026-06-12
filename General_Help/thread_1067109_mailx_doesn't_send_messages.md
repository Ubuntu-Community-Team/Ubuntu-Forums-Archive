---
title: "mailx doesn't send messages"
date: 2009-02-11
forum: General Help
---

### Post by pytheas22 on 2009-02-11
I installed mailx from the Ubuntu repositories but I can't get it to work.  I'm trying to send messages using a command like this:
```

echo "this is my message" | mailx -s "this is the subject line" email@domain.com
```

But emails are not showing up in the specified mailbox, and I'm not sure why (no error messages are mentioned in /var/log/mail.err).  I've tried sending to a couple different mail accounts from different providers.

When I installed the mailx package, I wasn't asked for any additional configuration information, so I assumed that it set everything up automatically.  Was that assumption wrong?  Do I need to edit some file to tell it how to send mail?

My network doesn't block any outgoing traffic, so I assume it's not being stopped there.  A lot of incoming ports are blocked on the router, but that shouldn't matter if I only want to send mail out, should it?

Thanks in advance for any advice on this--I would like to figure out how to make mailx work so that I can incorporate it into a script.

---

### Post by dcstar on 2009-02-12
> **pytheas22 said:**
> I installed mailx from the Ubuntu repositories but I can't get it to work.  I'm trying to send messages using a command like this:
```

echo "this is my message" | mailx -s "this is the subject line" email@domain.com
```

But emails are not showing up in the specified mailbox, and I'm not sure why (no error messages are mentioned in /var/log/mail.err).  I've tried sending to a couple different mail accounts from different providers.

When I installed the mailx package, I wasn't asked for any additional configuration information, so I assumed that it set everything up automatically.  Was that assumption wrong?  Do I need to edit some file to tell it how to send mail?

My network doesn't block any outgoing traffic, so I assume it's not being stopped there.  A lot of incoming ports are blocked on the router, but that shouldn't matter if I only want to send mail out, should it?

Thanks in advance for any advice on this--I would like to figure out how to make mailx work so that I can incorporate it into a script.

Install a MTA, like postfix.

---

### Post by pytheas22 on 2009-02-12
Thanks for the response.  I'll look into that.  It would make more sense if the mailx package depended on postfix if that's what it needs to work, however.

---

