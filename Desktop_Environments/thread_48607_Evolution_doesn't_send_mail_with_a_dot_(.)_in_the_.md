---
title: "Evolution doesn't send mail with a dot (.) in the address"
date: 2005-07-13
forum: Desktop Environments
---

### Post by Ferio on 2005-07-13
Well, the title is self-explaining, I can send mail to addresses like [email]xxxxxxxx@yyyyy.zzz[/email], but it doesn't allows me to send mail to addresses like [www.xxxx@yyyyy.zzz](www.xxxx@yyyyy.zzz). Has this happened to someone else? It's a bit annoying, 'cos I was using Thunderbird and it worked great, but I need something with the calendar/tasks feature included, and I dont like Thunderbird's Calendar plug-in.

---

### Post by manicka on 2005-07-13
I don't have that problem

---

### Post by Akoluth of Nandus on 2005-07-13
Does it give any error message?

---

### Post by Ferio on 2005-07-14
Yeah, I forgot about it, it's:

"RCPT TO <juan.diez.blanco@gmail.com> failed: Requested action not taken: mailbox name not allowed."

I've gone back to Thunderbird while this is solved...

---

### Post by manicka on 2005-07-14
Looks like a problem with the address at gmail rather than evolution

---

### Post by Ferio on 2005-07-14
No, I can send and receive from this address using Thunderbird or webmail, but I can't do it to the address of a friend of mine that has a dot, too.

---

### Post by manicka on 2005-07-14
That's strange. I don't have that problem with Evolution 2.2.1.1
What version do you have installed?

---

### Post by doclivingston on 2005-07-15
[QUOTE=Ferio]"RCPT TO <juan.diez.blanco@gmail.com> failed: Requested action not taken: mailbox name not allowed."[/QUOTE]
That's an SMTP error, which is from your (outgoing) mail server. If this is working in Thunderbird, but not Evolution, can you check that they are set to use the same SMTP server?

---

### Post by Ferio on 2005-07-15
I've been looking Gmail settings page, and they say that I won't be able to send mail with this account if my client hasn't SMTP authentication, which is the right one I must choose in the dropdown box?

---

### Post by doclivingston on 2005-07-15
The best way to check, is to select "Server requires authentication", and click "Check supported types". One this is done, anything that isn't supported will be crossed-out in the drop-down list.

---

### Post by Ferio on 2005-10-14
It seems it doesn't happen anymore with my new Breezy Badger. Thanks anyway!

---

