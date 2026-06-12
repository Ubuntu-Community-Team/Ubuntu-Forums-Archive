---
title: "Block read receipts in Evolution"
date: 2009-04-30
forum: General Help
---

### Post by lotsofish on 2009-04-30
I have Evolution set up to use my company's Exchange server. Works great, but I can't find a setting to disable sending read receipts. I don't want to tell people when I've read messages. How can I disable it in Evolution?

---

### Post by codeseer on 2009-04-30
> **lotsofish said:**
> I have Evolution set up to use my company's Exchange server. Works great, but I can't find a setting to disable sending read receipts. I don't want to tell people when I've read messages. How can I disable it in Evolution?

Edit->Preferences->Mail Accounts->Your Account->Edit->Defaults (At the bottom).

You'll also need to set mail to read as text only, because they can use image or code load traffic to determine when you read them as well. So, no HTML emails.

---

### Post by lotsofish on 2009-04-30
Hmmm, I saw that there, and it was already set to "Never" but they are still being sent. I just changed it to ask every time so I'll see if it asks.

---

### Post by codeseer on 2009-04-30
It's also on a per-account basis. How do you know they're being sent?

---

### Post by lotsofish on 2009-04-30
I just have the one account set up. I know they are being sent because my coworkers received them after I read a message they sent.

I just tried changing the read receipt option to "Ask me everytime", and it did ask me, however even when I said No, they still received a read receipt.

Also, I just logged into OWA because I know Evolution uses OWA to get and send messages and my account option is set for "Do not automatically send read receipts" in OWA settings.

---

### Post by codeseer on 2009-04-30
Well that's certainly odd. You are sure it's not your friend's providers doing it?

---

### Post by lotsofish on 2009-04-30
Found this [http://bugzilla.gnome.org/show_bug.cgi?id=530866](http://bugzilla.gnome.org/show_bug.cgi?id=530866) 

I guess it's known. I'll follow up on that bug report.

Thanks. :)

---

