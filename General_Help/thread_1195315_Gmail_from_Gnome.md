---
title: "Gmail from Gnome"
date: 2009-06-23
forum: General Help
---

### Post by catelee2u on 2009-06-23
Hi
Currently when I right click on a file in Gnome and select 'send to' a menu pops up with a dialog and Evolution is the default choice of application. I want it to default to a gmail setting where it would open a newly composed email in my gmail account in a new tab of firefox. I have used a script from here:
[http://www.howtogeek.com/howto/ubuntu/set-gmail-as-default-mail-client-in-ubuntu/](http://www.howtogeek.com/howto/ubuntu/set-gmail-as-default-mail-client-in-ubuntu/)
I followed this with the instructions for firefox opening Gmail in a new tab.

If I click send mail on a webpage it goes straight via Gmail but not from Gnome. I went through gconf-editor and set the mailto in urlhandlers to the script file but it didn't work. Help appreciated.

Thanks

---

### Post by fragos on 2009-06-23
You can configure Evolution to use the Gmail servers to send mail. The sent mail will show up in Gmail's Sent mail on the web. You will also need to tell Gmail to support IMAP. Not exactly what you asked for but it works.

---

### Post by jimv on 2009-06-23
That's interesting...mine says "Evolution" as well, but it opens up Thunderbird like it should.

---

### Post by catelee2u on 2009-06-23
Thanks Fragos. I already knew that actually but wanted it the other way. I always use webmail so I even removed Evolution when I first installed because it was unused. I'll see if I can get a solution/figure it out but if all else fails it'll be the way to go. :-)

I tried sending a file to see if it would go via Gmail even though it said Evolution but it just did nothing as Evolution is not installed.

---

### Post by jimv on 2009-06-23
Well, I followed those instructions and Send To opens Gmail, but it puts the attachment name in the To: box along with the email address.

---

### Post by RJ12 on 2009-06-23
> **jimv said:**
> Well, I followed those instructions and Send To opens Gmail, but it puts the attachment name in the To: box along with the email address.
I dont know if GNOME maybe supports using webmail

---

