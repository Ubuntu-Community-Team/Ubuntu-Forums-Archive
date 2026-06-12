---
title: "Deafault outgoing mail account in Thunderbird"
date: 2014-02-23
forum: Desktop Environments
---

### Post by karl12 on 2014-02-23
Hello,

I manage my emails with Thunderbirds several years now, but there is one particular irk that annoys me and that I could never really get rid off. I manage several accounts with Thunderbird where messages are received, but want to send emails just from one of the accounts. The default account was set via Edit -> Account settings -> select account -> account actions -> Set as default as well as via edit -> account settings -> outgoing server -> select account -> set as default.

However, when messages are forwarded or replied too that were received on an other than the default accouny the sender's address is not the default account, but the account which was the very first account that had been configured in Thunderbird. For the reply too address the default account is correctly set though.

Is this a bug or did I overlook a setting?

Any help is appreciated

---

### Post by CharlesA on 2014-02-23
I have always just selected whatever inbox of the address I want to compose an email from and that should cause TB to default to sending using that address.

---

### Post by buzzingrobot on 2014-02-24
Do you have more than one SMTP server configured?

---

### Post by karl12 on 2014-03-16
Yes, I have several accounts configured. And indeed, when selecting an account and then composing a message, the selected account is chosen to be send from. But that is not exactly what I want. I always want to send my outgoing emails from one fixed account. In particular when I reply to messages always the address is chosen on which the original message was received and not the account which is set as default.

---

### Post by SeijiSensei on 2014-03-16
If you control your own mail servers, this might work, but if you're using your providers' servers it probably won't.  Most mail providers only accept SMTP connections if the message uses a From addresses in a domain they host.  I don't think you can push a [email]user@hotmail.com[/email] message through GMail, for instance.  Any other arrangement leaves the provider vulnerable to becoming an open relay.

If you want all the replies to come to a specific mailbox, then use a "Reply-To" header.

You can tell Thunderbird to make one SMTP server the default for all outgoing mail, and you can use identities to control the From address you use.  I use both of these to send mail with various From addresses, but I'm using servers I manage myself.

---

