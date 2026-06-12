---
title: "How to use postfix sendmail command?"
date: 2009-04-02
forum: General Help
---

### Post by rhcm123 on 2009-04-02
I was using the basic exim4/sendmail on my lappy to send basic emails from my small server system. I recently revamped my server and installed postfix and courier, and removed exim4. I was used to using sendmail to send emails (it's terminal based) and i was wondering what the postfix equivalent of sendmail is, and how to use it.

---

### Post by dcstar on 2009-04-02
> **rhcm123 said:**
> I was using the basic exim4/sendmail on my lappy to send basic emails from my small server system. I recently revamped my server and installed postfix and courier, and removed exim4. I was used to using sendmail to send emails (it's terminal based) and i was wondering what the postfix equivalent of sendmail is, and how to use it.

It is sendmail.

---

### Post by HermanAB on 2009-04-02
$ mail -s "test message" [email]joe.soap@example.com[/email]
Yadda, yadda.
.

--

Remember that last dot.

The 'mail' command uses the 'sendmail' command which Postfix provides for convenience.

---

### Post by rhcm123 on 2009-04-05
> **HermanAB said:**
> $ mail -s "test message" [email]joe.soap@example.com[/email]
Yadda, yadda.
.

--

Remember that last dot.

The 'mail' command uses the 'sendmail' command which Postfix provides for convenience.

thank you much!

---

