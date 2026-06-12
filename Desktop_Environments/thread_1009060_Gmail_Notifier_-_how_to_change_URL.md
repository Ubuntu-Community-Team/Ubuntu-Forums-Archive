---
title: "Gmail Notifier - how to change URL?"
date: 2008-12-12
forum: Desktop Environments
---

### Post by teachmeifyoucan on 2008-12-12
Hi,

I'm running Ubuntu 8.10 and Firefox 3.0.4. I have the Gmail Notifier installed from gmail-notify.sourceforge.net. I live in Germany.

As you may already know, the "gmail.com" URL doesn't work when you're connected from Germany. For legal reasons, you must visit the address "mail.google.com".

My Gmail Notifier program correctly checks for new e-mail, but the shortcut to my inbox sends me to an error page.

How can I change the program so that it will run "mail.google.com" in my browser rather than "gmail.com"?

Thanks!

---

### Post by albandy on 2008-12-12
Use the package gmail-notify from the ubuntu repository.

Or if you want to continue using the one you've installed, edit the file gmailAtom.py and locate the the string "host", then change it to your desired value.

---

### Post by teachmeifyoucan on 2008-12-12
> **albandy said:**
> Use the package gmail-notify from the ubuntu repository.

Or if you want to continue using the one you've installed, edit the file gmailAtom.py and locate the the string "host", then change it to your desired value.

Albandy,

thanks for your quick response.

The package you mention is exactly what I already did install.

I have searched the filesystem for "gmailAtom.py" but there are 0 search results.

Please advise, thanks.

---

### Post by albandy on 2008-12-12
the file is in /usr/lib/gmail-notify/

I've edited the file and the references are to mail.google.com, but perhaps in your system are different.

If this not work we can do a little work-arround by editing the file /etc/hosts

---

### Post by teachmeifyoucan on 2008-12-12
> **albandy said:**
> the file is in /usr/lib/gmail-notify/

I've edited the file and the references are to mail.google.com, but perhaps in your system are different.

If this not work we can do a little work-arround by editing the file /etc/hosts

Thanks, Albandy. I found the file and opened it.

My version also points to "https://mail.google.com". Strange.

I've opened the /ets/hosts file you mentioned but there is no reference to Google there.

---

### Post by albandy on 2008-12-12
Please, open it from the console: gmail-notify
then paste all the console output here.

---

### Post by teachmeifyoucan on 2008-12-12
> **albandy said:**
> Please, open it from the console: gmail-notify
then paste all the console output here.


username@computer:~$ gmail-notify
Gmail Notifier v1.6.1b (2008/12/12 13:51:33)
----------
xmllangs: XML file succesfully parsed
Configuration read (/home/username/.notifier.conf)
selected language: English
connecting...
connection successful... continuing
----------
checking for new mail (2008/12/12 13:51:33)
no new messages
----------
checking for new mail (2008/12/12 13:51:54)
no new messages

---

### Post by albandy on 2008-12-12
It's working perfect. There are no unread messages so it don't notify.
You should see a envelope near to system clock

---

### Post by teachmeifyoucan on 2008-12-12
> **albandy said:**
> It's working perfect. There are no unread messages so it don't notify.
You should see a envelope near to system clock

Yes, I already said that it was working. What *isn't* working is the "Go to inbox" shortcut that appears when you right click the envelope icon.

When I click this shortcut, it sends me to gmail.com, which in turn gives me the error message that I cannot visit gmail.com from Germany, but must point my browser to mail.google.com instead.

What I want to do is *change* the shortcut so that it sends me to mail.google.com in the first place.

---

### Post by albandy on 2008-12-12
Ah ok, so edit this file: /usr/lib/gmail-notify/notifier.py and change gmail.google.com to mail.google.com

---

### Post by teachmeifyoucan on 2008-12-12
> **albandy said:**
> Ah ok, so edit this file: /usr/lib/gmail-notify/notifier.py and change gmail.google.com to mail.google.com

Hooray! It works now. Thanks!

---

