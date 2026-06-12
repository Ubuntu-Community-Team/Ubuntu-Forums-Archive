---
title: "My laptop seems to be trying to send mail that I am unaware of"
date: 2009-04-01
forum: General Help
---

### Post by Mickser_52 on 2009-04-01
My laptop is running Ubuntu and Xp on a dual boot. I notice today, by accident, that it appears to be trying to send mail.

The Mail.warn and Mail.error archive going back to February up to today gives the following:

[Feb 22 18:39:58 michael-laptop nullmailer[9328]: smtp: Failed: Connect failed
Feb 22 18:39:58 michael-laptop nullmailer[5408]: Sending failed:  Host not found]

and the mail.log with archives going back to March has the following:


[Mar 12 16:27:36 michael-laptop nullmailer[5247]: Rescanning queue.
Mar 12 16:27:36 michael-laptop nullmailer[5247]: Starting delivery: protocol: smtp host: mail. file: 1236547689.14407
Mar 12 16:27:36 michael-laptop nullmailer[10045]: smtp: Failed: Connect failed
Mar 12 16:28:37 michael-laptop nullmailer[5247]: Sending failed:  Host not found
Mar 12 16:28:37 michael-laptop nullmailer[5247]: Delivery complete, 7 message(s) remain.]

I am not sure what caused this problem and it does not seem to effect the computer in any noticeable way. 

Is there some way to clear a queue which seems to have built up.

The messages are continuing to appear in the log but the number 7 has not increased.

---

### Post by ibuclaw on 2009-04-01
Try installing a mail app, ie:
```
sudo apt-get install mailx
```
Then export the variable MBOX (**note: order is essential here**)
```
export MBOX="$HOME/.local/mbox"
echo $!! >> ~/.bashrc

```
Then to retrieve the mail, type in **mail**
```
mail
```
Usually, it's just the output from a cronjob (which is a routinely ran task to keep certain things up-to-date).

Regards
Iain

---

### Post by Mickser_52 on 2009-04-01
Thanks for your reply. I have just found out that this is not a new problem and seems to be associated with nullmailer. The advice I have read so far was to uninstall nullmailer.

I have just removed the nullmailer queue directory from /var/spool/nullmailer/queue and so far the messages which were comming about 30 to the minute have stopped.

---

