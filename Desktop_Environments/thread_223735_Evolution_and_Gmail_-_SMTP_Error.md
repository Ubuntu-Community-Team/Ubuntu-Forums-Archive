---
title: "Evolution and Gmail - SMTP Error"
date: 2006-07-26
forum: Desktop Environments
---

### Post by jISh on 2006-07-26
I have followed many guides on setting up my Gmail account in Evolution.
I can connect and revieve my mail just fine, but when I try to send mail, it says "Bad authentication response from server". I have it using SSL encryption and PLAIN.

Any ideas?

---

### Post by wjp.reg on 2006-07-26
Did you check to ensure you have the right username and password? I know gmail needs you to provide that in order to send.  You may also have to assign a port for SMTP, I've used 587 or 465.  I think the newer versions of evolution don't require this but you might want to try it.

e.g. smtp.gmail.com:587

good luck

---

### Post by shawnrgr on 2006-07-26
actually, just starting today, ive not been able to send mail through gmail when its on both html/plain text. to someone who I've always been able to. maybe they are having server issues today. try again tomorrow.

---

### Post by donkE on 2008-02-15
smtp.gmail.com:587 worked for me too after trying every other possible option. seems weird that :465 doesn't work. any ideas? 

thanks.

---

