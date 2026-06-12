---
title: "Poll remote POP, put into IMAP Server"
date: 2006-07-21
forum: Desktop Environments
---

### Post by SuperJason on 2006-07-21
I would like to set up a local mail server.  Is it possible to somehow check my remote pop accounts (fetchmail?) and then put those emails into an IMAP server so that I can browse them from multiple computers?

If you could just point me in the right director for the software I would need, I would appreciate it.

I'm trying to convert a lot of our infrastructure over to Ubuntu server.

---

### Post by mannheim on 2006-07-21
I have used getmail (as a cron job) to fetch mail from a server and deliver it to my machine. Soon I decided that using a .forward file in my account on the server was a cleaner solution.

I don't know if either of these is applicable to your situation, particularly as I am dealing with just a single user (me).

---

### Post by xrado on 2006-07-24
im also interested how to Poll remote POP, put into IMAP Server if some one knows how?

---

### Post by SuperJason on 2006-08-09
> **xrado said:**
> im also interested how to Poll remote POP, put into IMAP Server if some one knows how?

I did get this working how I wanted.  I posted some details to my blog:
[http://www.superjason.com/archive/2006/08/09/Polling_Remote_POP3_Servers_for_Mail_and_pushing_into_Linux_IMAP_Server.aspx]("http://www.superjason.com/archive/2006/08/09/Polling_Remote_POP3_Servers_for_Mail_and_pushing_into_Linux_IMAP_Server.aspx")

---

### Post by jazzi on 2006-08-18
> **mannheim said:**
> I have used getmail (as a cron job) to fetch mail from a server and deliver it to my machine. Soon I decided that using a .forward file in my account on the server was a cleaner solution.

I don't know if either of these is applicable to your situation, particularly as I am dealing with just a single user (me).

I am using getmail,It said that it's the replacement of fetchmail.

But,I can't make getmail to work.and my account is gmail.

Do somebody know how to pop3 mail from gmail?

---

