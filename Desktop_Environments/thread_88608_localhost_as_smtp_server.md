---
title: "localhost as smtp server"
date: 2005-11-10
forum: Desktop Environments
---

### Post by ryke on 2005-11-10
hi,

with hoary, I had set my localhost (127.0.0.1) as smtp server and everything worked ok (in fact, I still have 1 of my computers with Hoary and it's working ok).

but with breezy it doesn't work... I have to use as smtp server the settings of one of my several accounts (and the problem is that data from the account used as smtp appears in the message and can be viewed by the receiptor)

any help about how to do?

thanx in advance ;-)

(I use thunderbird)

---

### Post by ryke on 2005-11-10
hi,

well, after installing postfix everything is ok :-)

---

### Post by YaseenKriel on 2006-11-14
i would like a similar setup on my pc but i can not find instructions in this forum on how to setup smtp on localhost. Could someone please provide me a link or instructions on how to do this please? i am using edgy eft on a notebook and would like to use evolution as my client.

Are these instructions good enough?

[http://www.howtoforge.com/perfect_setup_ubuntu_6.10_p5](http://www.howtoforge.com/perfect_setup_ubuntu_6.10_p5)

---

### Post by dcstar on 2006-11-14
> **YaseenKriel said:**
> i would like a similar setup on my pc but i can not find instructions in this forum on how to setup smtp on localhost. Could someone please provide me a link or instructions on how to do this please? i am using edgy eft on a notebook and would like to use evolution as my client.
......

I did this in Dapper & Breezy:

[LIST=1]
[*]Install the postfix package
[*]Edit /etc/postfix/main.cf to add in your own myhostname entry (it has to be a valid domain as some SMTP servers reject non-valid ones).
[*]In Evolution, in the Preferences of your e-mail account(s) select "Sendmail" for the Sending Server type
[*]Start using e-mail!
[/LIST]
All mail I send goes to the local postfix for direct delivery to the destination SMTP servers, so I'm now independent of any ISP's mail server for sending mail.

You can check status of outgoing messages using "mailq" and other postfix/sendmail utilities.

---

### Post by YaseenKriel on 2006-11-14
thanx for info, i installed postfix and but my emails are sitting in my mail queue and not going anywhere. Not sure what to change to get them moving.

---

### Post by dcstar on 2006-11-15
> **YaseenKriel said:**
> thanx for info, i installed postfix and but my emails are sitting in my mail queue and not going anywhere. Not sure what to change to get them moving.

Have a look at your mail.log and see if there are any relevant messages.

---

