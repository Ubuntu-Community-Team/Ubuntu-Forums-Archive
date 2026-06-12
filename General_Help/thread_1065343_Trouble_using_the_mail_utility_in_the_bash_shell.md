---
title: "Trouble using the mail utility in the bash shell"
date: 2009-02-09
forum: General Help
---

### Post by connor on 2009-02-09
I'm trying to use the mail utility to send email through the command line. I'm a grad student and I eventually want to write a shell script to do my grading and send students their grades, but I'm stumped on the mail utility. The tutorials on the net make it look really easy.

$ MAIL="me@addy.com"
$ MSG="msg.txt"
$ SUBJ="Subject"
$ mail -s "$SUBJ" "$MAIL" < "$MSG"

I never receive anything in my in-box. Any ideas?

Thanks,
Connor

---

### Post by cmnorton on 2009-02-14
I could be wrong, but I believe you need sendmail installed and running to deliver your mail.

---

### Post by HermanAB on 2009-02-14
You got to install Postfix, Qmail, Zimbra or Citadel first.

Cheers,

Herman

---

