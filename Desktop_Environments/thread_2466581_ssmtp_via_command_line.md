---
title: "ssmtp via command line"
date: 2021-08-31
forum: Desktop Environments
---

### Post by Geoff_Lane on 2021-08-31
After a wee bit of trial and error I have been able to send something using ssmtp via the terminal.

Oddly the body does not get copied.

ssmtp <an email recipient>
Subject:Test
From:<my email address>  **Needed this otherwise reports sender not authorised**
Hello World
GL

<ctrl-d>

Successfully sent but the email received shows the Subject line, who it is from but no body?

I seem to remember from my old BBS days that sending an email via the board required certain trigger comments but I don't recall anything specific from the message body.

Any suggestions appreciated.

Geoff

---

### Post by Geoff_Lane on 2021-08-31
Think I've sorted it, seems there needs to be a blank line after the Subject: entry.

Found this advice under instructions for sending mail via telnet, can't say as I've seen it mentioned under usage for ssmtp

Geoff

---

