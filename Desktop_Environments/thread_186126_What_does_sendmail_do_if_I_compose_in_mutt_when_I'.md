---
title: "What does sendmail do if I compose in mutt when I'm offline?"
date: 2006-06-01
forum: Desktop Environments
---

### Post by rosslaird on 2006-06-01
Sometimes, I'd like to be able to write emails in mutt while I'm away from an internet connection (I can update my mail with offlineimap before going offline). Since mutt does not actually send mail but relies instead on sendmail (I believe), what will happen to the mails sent from mutt if I'm not connected? Will sendmail queue them, and send them when connected, or will they be discarded?

Thanks.

Ross

---

### Post by JoWilly on 2006-06-01
Yep, mail goes to the mail queue in /var.

---

### Post by rosslaird on 2006-06-01
Thanks for the reply. 
Do I need to run "sendmail -q" to flush the queue, or will sendmail do this automagically upon reconnect?

R.

---

