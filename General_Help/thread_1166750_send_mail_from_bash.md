---
title: "send mail from bash"
date: 2009-05-22
forum: General Help
---

### Post by b-boy on 2009-05-22
Hi guys 


How can I send a mail from bash to my exchange email address?

---

### Post by glotz on 2009-05-22
Check out the **mailutils** package.

---

### Post by gooligan on 2009-05-22
Try ssmtp. it is available from universe. Very simple to use. See Howto below
[http://tombuntu.com/index.php/2008/10/21/sending-email-from-your-system-with-ssmtp/](http://tombuntu.com/index.php/2008/10/21/sending-email-from-your-system-with-ssmtp/)

---

### Post by tornadof3 on 2009-05-22
Dead easy. Ensure the "mailutils" package is installed (sudo apt-get install mailutils) and then use the "mail" command:

```
mail -s "Your Subject"

This is my message

.
```

Finish with a dot (.) on the last line. Job done! This assumes sendmail is correctly set up of course...

---

