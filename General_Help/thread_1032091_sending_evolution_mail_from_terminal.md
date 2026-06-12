---
title: "sending evolution mail from terminal"
date: 2009-01-06
forum: General Help
---

### Post by das867 on 2009-01-06
hi, i'm kind of new to linux (8 monthes), and i was wondering, is it possible to send evolution mail from the terminal. what i need is the knowledge to create a shell script without any input from the user (stdin i guess?). if anyone could help me with that, that would be amazing. and yes, i've tried the mail command, but i cant figure out how to configure it to send to an external email address, like [email]somebody@gmail.com[/email] for example.

---

### Post by das867 on 2009-01-06
bump?

---

### Post by jrusso2 on 2009-01-06
There are commandline email programs like Pine, Elm etc that are more fit for this.

---

### Post by das867 on 2009-01-06
> **jrusso2 said:**
> There are commandline email programs like Pine, Elm etc that are more fit for this.

But can i make a shell script to send mail with them?

---

### Post by das867 on 2009-01-06
Bump?

---

### Post by linux_tech on 2009-01-06
This article may be of some help-
[http://www.macosxhints.com/article.php?story=20081217161612647](http://www.macosxhints.com/article.php?story=20081217161612647)

---

### Post by kaspar_silas on 2011-02-03
Sort of late but better than never.

Use sendemail (Note the e Not sendmail) its the simplest.

An example usage:

$ sendemail -f [email]from@mail.com[/email] -t [email]to@mail.com[/email] -u "subject" -m "Well, hello." -s server.com -xu loginName -xp loginPassword 

More options here:
[http://www.debianadmin.com/how-to-sendemail-from-the-command-line-using-a-gmail-account-and-others.html]("http://www.debianadmin.com/how-to-sendemail-from-the-command-line-using-a-gmail-account-and-others.html")

---

